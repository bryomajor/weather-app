<template>
  <div class="weather-wrap" v-if="weather.main != undefined">
    <location-box :now="now" :weather="weather" />
    <weather-box :weather="weather" />
  </div>
</template>

<script>
import LocationBox from './LocationBox';
import WeatherBox from './WeatherBox';

export default {
  components: {
    LocationBox,
    WeatherBox
  },
  props: {
    weather: {
      type: Object,
      required: true
    },
    now: {
      type: Object,
      required: true
    }
  }
}
</script>
