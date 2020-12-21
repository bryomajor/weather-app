<template>
  <div id="app" :class="typeof weather.main != 'undefined' && weather.main.temp > 16 ? 'warm' : ''">
    <main>
      <search-box :fetchWeather="fetchWeather" @update-search-term="updateSearchTerm" />
      <weather-wrap :now="now" :weather="weather" />
    </main>
  </div>
</template>

<script>

const moment = require('moment');

import SearchBox from './components/SearchBox';
import WeatherWrap from './components/WeatherWrap';

export default {
  name: 'App',
  data() {
    return {
      api_key: 'e904ef0126639cc0e9d4bc215bc152cc',
      url_base: 'https://api.openweathermap.org/data/2.5/',
      query: '',
      weather: {},
      now: moment()
    }
  },
  components: {
    SearchBox,
    WeatherWrap
  },
  methods: { 
    updateSearchTerm(term) {
      this.query = term;
    },
    fetchWeather() {
      fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
      .then(res => {
        return res.json();
      }).then(this.setResults)
      .catch(err => {
        console.warn(err);
      });
    },
    setResults(results) {
      this.weather = results;
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box
}

body {
  font-family: 'Montserrat', sans-serif;
}

#app {
  background-image: url('./assets/cold-bg.jpg');
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
}

#app.warm {
  background-image: url('./assets/warm-bg.jpg'); 
}

main {
  min-height: 100vh;
  padding: 25px;
  background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0.25), rgba(0, 0, 0, 0.75));
}
</style>
