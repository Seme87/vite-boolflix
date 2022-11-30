<script>
import AppCardMovie from "./AppCardMovie.vue";

import { store } from "../store.js";

export default {
  name: "AppMain",
  components: {
    AppCardMovie,
  },
  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <main class="container d-flex">
    <AppCardMovie :info="store.movie" v-for="movie in store.movies" />
  </main>
</template>

<style lang="scss" scoped>
h2 {
  color: gold;
}
</style>
