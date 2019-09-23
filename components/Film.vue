<template>
    <div class="row justify-content-center pt-4">
        <div class="col-9 film">
            <div class="row p-3">
              <div class="col-12 text-center">
                <h3>{{ title }}</h3>
              </div>
            </div>
            <div class="row">
                <div class="col-12 col-md-7 pl-5">
                    <p>{{ text }}</p>
                </div>
                <div class="col d-flex align-items-center justify-content-center poster">
                    <a :href="`images/${id}.jpg`">
                        <img class="img-fluid" :src="`images/${id}.jpg`" />
                    </a>
                </div>
                <div class="col-12 my-3 d-flex align-items-center justify-content-center">
                    <button @click="infoPage" class="btn-custom">More Info</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    head: {
        titleTemplate: 'Films List'
    },
    props: ['title', 'text', 'url', 'id'],
    methods: {
        infoPage() {
            const filmIndex = this.url.slice(21);
            this.$router.push({
                path: filmIndex
            })
        }
    }
}
</script>

<style scoped>
    h3 {
        color: yellow;
        text-decoration: none;
        cursor: pointer;
    }
    .film {
        background: #282727;
        color: white;
        border-radius: 10px;
    }
    .film p {
        font-size: 16px;
    }
    .poster img {
        height: 180px;
        max-width: 100%;
        box-shadow: 5px 4px 11px 0px silver;
    }
    .btn-custom {
        padding: 10px 15px;
        background: none;
        outline: none;
        border: 1px solid silver;
        color: white;
        border-radius: 8px;
        text-transform: uppercase;
    }
    .film_wrapper {
        position: relative;
    }
    .film .row::after {
        content: '';
        position: absolute;
        height: 60px;
        width: 10px;
        top: 40%;
        border-radius: 0px 20px 20px 0px;
        left: 0px;
        background: #151515;
    }
</style>
