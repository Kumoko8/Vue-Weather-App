<template>
  <img alt="angry thundercloud logo" src="./assets/WeatherApp.png">
  <Forecast msg="Weather Forecast"/>
</template>

<script>
import Forecast from './components/Forecast.vue'

export default {
  name: 'App',
  components: {
    Forecast
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
img {
  width: 20em;
  border-radius: 50%;
}
</style>
