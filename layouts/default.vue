<template>
  <div class="no-focus-outline">
    <nuxt/>
  </div>
</template>

<script>
export default {
  head: {
    titleTemplate: 'Star War Films',
    meta: [
      { charset: 'utf-8' },
      { name: 'viewport', content: 'width=device-width, initial-scale=1' },
      { hid: 'description', name: 'description', content: 'Meta description' }
    ]
  }
}
</script>

<style>
  body {
    padding: 0;
    font-family: 'Amiri', serif;
    margin: 0;
    background: #151515;
    /* background: url('/images/sky.jpg') center center fixed; */
    background-repeat: no-repeat;
  }
  .no-focus-outline a:focus,
  .no-focus-outline button:focus {
    outline: none;
  }
</style>

