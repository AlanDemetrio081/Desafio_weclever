<template>
  <div id="app">
    <div class="card">
      <div v-for="(star, index) in starw" :key="star.url">
        <Star
          :name="star.name"
          :films="star.films"
          :url="star.url"
          :pleope="index + 1"
        />
      </div>
    </div>
  </div>
  
</template>

<script>
import Star from "./components/Star.vue";
import axios from "axios";
export default {
  name: "app",
  data() {
    return {
      offset: 1,
      starw: [],
    };
  },
  created: function () {
    const base = "https://swapi.dev/api";
    const urls = `${base}/people/?limit=$83&page=${this.offset}&offset=0`;
    axios.get(urls).then((res) => {
      this.starw = res.data.results;
    });
  },
  components: {
    Star,
  },
  
};
</script>
<style>
#app {
    align-items:center;
    justify-content: center;
   
}

#page {
  margin-left: 75vh;
}
</style>