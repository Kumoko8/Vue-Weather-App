<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <section>
      <h2>Current Weather</h2>
      <section id="current-weather">
        <div v-if="currentWeather">
          <h3>{{ currentWeather.name }}</h3>
          <p>{{ currentWeather.weather[0].description }}</p>
          <p>Temperature: {{ currentWeather.main.temp }}°C</p>
          <p>Wind Speed: {{ currentWeather.wind.speed }} m/s</p>
        </div>
      </section>
    </section>
    <section>
      <h2>5 Day Forecast</h2>
      <section id="five-day">
        <div v-for="forecast in fiveDayForecast" :key="forecast.dt">
          <div>Date: {{ new Date(forecast.dt * 1000).toLocaleDateString() }}</div>
          <div>Temperature: {{ forecast.main.temp }}°C</div>
          <div>Wind Speed: {{ forecast.wind.speed }} m/s</div>
        </div>
      </section>
    </section>
    <section class="search">
      <input v-model="city" type="text" placeholder="Type city name" />
      <button @click="searchWeather" type="submit">Search</button>
    </section>

    <h4>Search History</h4>
    <section id="hist">
      <!-- Display search history here -->
      <div v-for="historyItem in searchHistory" :key="historyItem">
        {{ historyItem }}
      </div>
    </section>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  data() {
    return {
      city: '',
      currentWeather: null,
      fiveDayForecast: [],
      searchHistory: [],
    };
  },
  methods: {
    async searchWeather() {
      try {
        // Fetch current weather
        const currentWeatherResponse = await axios.get(
          'https://api.openweathermap.org/data/2.5/weather',
          {
            params: {
              q: this.city,
              appid: '06749fe30c18e7dfb4329c7f75e760bc"',
              units: 'metric',
            },
          }
        );
        this.currentWeather = currentWeatherResponse.data;

        // Fetch 5-day forecast
        const forecastResponse = await axios.get(
          'https://api.openweathermap.org/data/2.5/forecast',
          {
            params: {
              q: this.city,
              appid: 'YOUR_OPENWEATHERMAP_API_KEY',
              units: 'metric',
            },
          }
        );
        this.fiveDayForecast = forecastResponse.data.list;

        // Update search history
        this.searchHistory.unshift(this.city);
        if (this.searchHistory.length > 5) {
          this.searchHistory.pop();
        }
      } catch (error) {
        console.error('Error fetching weather data', error);
      }
    },
  },
};
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

using API

installed axios
imported code