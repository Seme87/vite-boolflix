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
    <AppCardMovie
      class="ms-appcard"
      :info="movie"
      v-for="movie in store.movies"
    />
  </main>
</template>

<style lang="scss" scoped>
main {
  flex-wrap: wrap;
}
.ms-appcard {
  padding: 10px;
  width: calc(100% / 5);
}
</style>
