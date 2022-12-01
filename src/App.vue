<script>
import { store } from "./store";
import axios from "axios";

import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";

export default {
  components: {
    AppHeader,
    AppMain,
  },
  data() {
    return {
      store,
    };
  },
  methods: {
    onGetMovie() {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: "f0fb5f5dcb06636c7f99f213e5ae5cd2",
            query: store.searchText,
            language: "it-IT",
          },
        })
        .then((res) => {
          console.log(res.data.results);
          this.store.movies = res.data.results;
        });
    },
    onGetSeries() {
      axios
        .get("https://api.themoviedb.org/3/search/tv", {
          params: {
            api_key: "f0fb5f5dcb06636c7f99f213e5ae5cd2",
            query: store.searchText,
            language: "it-IT",
          },
        })
        .then((res) => {
          console.log(res.data.results);
          this.store.series = res.data.results;
        });
    },
    getData() {
      this.onGetMovie();
      this.onGetSeries();
    },
  },
};
</script>

<template>
  <div>
    <AppHeader @performSearch="getData" />
    <AppMain />
  </div>
</template>

<style lang="scss">
@import "./style/global.scss";
</style>
