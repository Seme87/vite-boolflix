<script>
import AppCardMovie from "./AppCardMovie.vue";

import { store } from "../store.js";
import AppCardSeries from "./AppCardSeries.vue";

export default {
  name: "AppMain",
  components: {
    AppCardMovie,
    AppCardSeries,
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
    <AppCardSeries
      class="ms-appcard"
      :infoSeries="serie"
      v-for="serie in store.series"
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
