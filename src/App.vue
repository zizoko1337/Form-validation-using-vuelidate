<template>
  <img class="logo" src="./assets/logotype.png">
  <VueForm msg="Welcome to Your Vue.js App"/>
</template>

<script>
import VueForm from './components/VueForm.vue'

export default {
  name: 'App',
  components: {
    VueForm
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.logo {
  max-height: 20vh;
}
</style>
