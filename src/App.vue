<template>
  <div id="app">
    <img alt="Vue logo" src="@/assets/pokemon.jpeg">
    <PokeComponent></PokeComponent>
  </div>
  
</template>

<script>
import PokeComponent from './components/PokeComponent.vue'

export default {
  name: 'App',
  components: {
    PokeComponent
  }
}
</script>

<style>
body{
  background-color: rgba(238, 238, 238, 0.582);
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
