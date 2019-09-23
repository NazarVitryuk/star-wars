<template>
    <div class="row header">
        <div class="col-12 col-md-auto logo">
            <nuxt-link class="d-flex flex-column align-items-center" to="/">
                <img src="/images/sw_logo_horiz-04368052e188.png" />
                <p class="mb-0">Films Info</p>
            </nuxt-link>
        </div>
        <div class="col-6 col-md-auto justify-content-center link d-flex align-items-center ml-md-auto">
            <nuxt-link to="/">Home</nuxt-link>
        </div>
        <div class="col-6 col-md-auto justify-content-center link d-flex align-items-center">
            <nuxt-link to="/films">Films List</nuxt-link>
        </div>
    </div>
</template>

<script>
export default {

}
</script>

<style scoped>
    .header {
        padding: 15px 0px;
    }
    .logo {
        color: white;
    }
    .logo a {
        font-size: 25px;
        font-weight: bolder;
        text-transform: uppercase;
        text-decoration: none;
        color: deepskyblue;
    }
    .logo img {
        width: 190px;
        height: 30px;
    }
    .link a {
        color: deepskyblue;
        font-size: 25px;
        text-decoration: none;
        border-bottom: 2px solid transparent;
    }
    .link a:hover {
        border-bottom: 2px solid yellow;
    }
</style>
