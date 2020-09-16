<template>
  <div
      id="app"
      class="container-fluid"
  >
    <Beggar head="Money for honey"/>
  </div>
</template>

<script>
import Beggar from './components/Beggar.vue'

export default {
  name: 'App',
  components: {
    Beggar
  }
}
</script>

<style>
body {
  background-color: #f3c928;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  background-color: #f3c928;
  margin-top: 60px;
}

h1 {
  text-align: center;
}
</style>
