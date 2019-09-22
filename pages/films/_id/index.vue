<template>
  <div class="container-fluid">
    <Header />
    <div class="row justify-content-center">
      <div class="col-6 mb-5 text-center film_name">
        {{ filmData.title }}
      </div>
    </div>
    <div class="row film_content mb-5">
      <div class="col-4 d-flex justify-content-center film_image">
        <img class="img-fluid" :src="`/images/${ filmData.episode_id }.jpg`" />
      </div>
      <div class="col-7">
        <span class="film_info">Title:</span>
        <span>{{ filmData.title }}</span>
        <br />
        <span class="film_info">Director:</span>
        <span>{{ filmData.director }}</span>
        <br />
        <span class="film_info">Release Date:</span>
        <span>{{ filmData.release_date }}</span>
        <br />
        <span class="film_info">Producer:</span>
        <span>{{ filmData.producer }}</span>
        <br />
        <span class="film_info">Opening Crawl:</span>
        <span>{{ filmData.opening_crawl }}</span>
      </div>
    </div>
  </div>
</template>

<script>
import Header from '../../../components/Header'

export default {
    head: {
        titleTemplate: 'Film Info'
    },
    components: {
        Header
    },
    // fetch film data by id
    async asyncData({route}) {
        const res = await fetch(`https://swapi.co/api/films/${route.params.id}`);
        const filmData = await res.json();

        return {filmData}
    }
}
</script>

<style>
    .film_image img {
        width: 70%;
        height: 100%;
        box-shadow: 5px 4px 11px 0px silver;
    }
    .film_content {
        color: white;
        font-size: 25px;
    }
    .film_name {
        margin: 10px 0;
        padding: 10px 0;
        background: #282727;
        border-radius: 5px;
        font-size: 25px;
        font-weight: bolder;
        color: deepskyblue;
    }
    .film_info {
        font-size: 30px;
        font-weight: bolder;
        color: deepskyblue;
    }
</style>