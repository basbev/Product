<template>
  <div id="app" class="img-resize">
    <img src="./assets/product.jpg">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}
div.img-resize img {
  width: 350px;
  height: 200px;
}

</style>
