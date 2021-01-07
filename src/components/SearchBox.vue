<template>
  <div class="search-box">
    <input
      type="text"
      class="search-bar"
      placeholder="Enter location to see it's weather conditions..."
      v-model="query"
      @keyup.enter="fetchWeather"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      query: this.term
    }
  },
  watch: {
    query: {
      handler() {
        this.$emit("update-search-term", this.query);
      }
    }
  },
  props: {
    fetchWeather: {
      type: Function
    },
    term: {
      type: String
    }
  }
}
</script>

<style scoped>
.search-box {
  width: 100%;
  margin-bottom: 30px;
}

.search-box .search-bar {
  display: block;
  width: 100%;
  padding: 15px;

  color: #313131;
  font-size: 20px;

  appearance: none;
  border: none;
  outline: none;
  background: none;

  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 0px 16px 0px 16px;
  transition: 0.4s;
}

.search-box .search-bar:focus {
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.75);
  border-radius: 16px 0px 16px 0px;
}
</style>