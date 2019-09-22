<template>
  <div class="container-fluid">
    <Header />
    <div class="row">
      <div class="col d-flex justify-content-center film_search">
        <input type="text" v-model="searchText" @input="onFilmSearch" placeholder="Search" />
      </div>
    </div>
    <div :key="item.episode_id" v-for="item in collection">
      <Film
        v-if="item.title.toLowerCase().indexOf(searchText.toLowerCase()) >= 0"
        :id="item.episode_id"
        :url="item.url" 
        :title="item.title" 
        :text="item.opening_crawl"></Film>
    </div>
    <div v-if="searchText == ''" class="row my-5 pagi_wrapper">
      <div class="col-12 d-flex justify-content-center">
          <button 
            class="pagi_btn"
            v-bind:class="{'active':(i == activeButton)}"
            v-for="(p, i) in pagination.pages"
            :data-id="i"
            @click.prevent="setPage(p)"
            @click="setActiveButton(i)"
            :key="p">
            {{ p }}
          </button>
    </div>
  </div>
  </div>
</template>

<script>
import Header from '../../components/Header'
import Film from '../../components/Film'
import _ from 'lodash'

export default {
components: {
    Header,
    Film
  },
  data() {
    return {
      perPage: 2,
      pagination: {},
      searchText: '',
      activeButton: 0,
    }
  },
  async asyncData() {
    const res = await fetch('https://swapi.co/api/films/')
    const films = await res.json()
    return {
      films: films.results
    }
  },
  computed: {
      collection() {
        return this.searchText !== '' ? this.onFilmSearch() : this.paginate(this.films)
      }
  },
  methods: {
    onFilmSearch() {
      return this.films.filter(film => film.title.toLowerCase().indexOf(this.searchText) >= 0)
    },
    setActiveButton(i) {
      this.activeButton = i;
    },
    setPage(p) {
      this.pagination = this.paginator(this.films.length, p)
    },
    paginate(data) {
      return _.slice(data, this.pagination.startIndex, this.pagination.endIndex + 1)
    },
    paginator(totalItems, currentPage) {
      var startIndex = (currentPage - 1) * this.perPage,
      endIndex = Math.min(startIndex + this.perPage - 1, totalItems - 1);

      return {
        currentPage: currentPage,
        startIndex: startIndex,
        endIndex: endIndex,
        pages: _.range(1, Math.ceil(totalItems / this.perPage) + 1)
      };
    } 
  },
  created() {
    this.setPage(1)
  }
}
</script>

<style>
.pagi_btn {
    margin: 5px;
    outline: none;
    width: 40px;
    height: 35px;
    border: 1px solid deepskyblue;
    background: none;
    border-radius: 20px;
    color: white;
  }
  .active {
    background: yellow;
    color: black;
    border: 0;
  }
  .film_search input {
    background: #282727;
    border: 1px solid #656565;
    padding: 10px 0 10px 5px;
    color: white;
    border-radius: 5px;
    outline: none;
  }
</style>