<template>
  <div class="container-fluid">
    <Header />
    <div class="row">
      <div class="col logo-text text-center">
        <h2>Welcome to Star Wars Film Info Site</h2>
      </div>
    </div>
    <div class="row justify-content-center">
      <div class="col-auto">
        <div class="logo-link">
          <nuxt-link to="/films">
            <h3 class="mt-3">Go to Films List</h3>
          </nuxt-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Header from '../components/Header'

export default {
  components: {
    Header
  }
}
</script>

<style>
  .logo-text {
    color: white;
    font-size: 25px;
  }
  .logo-text h3 {
    color: deepskyblue;
  }
  .logo-link a {
    text-decoration: none;
    color: deepskyblue;
  }
  .logo-link:hover {
    border-bottom: 2px solid yellow; 
  }
</style>

