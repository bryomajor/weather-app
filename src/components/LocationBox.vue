<template>
  <div class="location-box">
    <div class="location">{{ weather.name }}, {{ weather.sys.country }}</div>
    <div class="date">{{ now.format("dddd, Do MMMM YYYY") }}</div>
  </div>
</template>

<script>
export default {
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

<style scoped>
.location-box .location {
  color: #FFF;
  font-size: 32px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25)
}

.location-box .date {
  color: #FFF;
  font-size: 20px;
  font-weight: 300;
  font-style: italic;
  text-align: center;
}
</style>