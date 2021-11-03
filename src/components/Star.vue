<template>
    <div class="card-content">
      <div class="media">
        <div class="media-content">
          <p class="title is-4">{{ people }} - {{ name }}</p>
        </div>
      </div>
      <div class="content">
        <p v-if="show" class="subtitle is-6">{{ films }}</p>
        <button @click="click" class="button is-danger">Filmes</button>
      </div>
      <hr>
    </div>
</template>

<script>
import axios from "axios";
export default {
  created: function () {
    axios.get(this.url).then((res) => {
      this.star.type = res.data.type[0].type.name;
      this.star.films_ = res.data.films_[0].films_.films;
    });
  },
  data() {
    return {
      show: false,
      films_: "",
      star: {
        type: "",
        films: "",
      },
    };
  },
  props: {
    name: String,
    films: String
  },
  methods: {
    click() {
      this.show = !this.show;
    },
  },
};
</script>