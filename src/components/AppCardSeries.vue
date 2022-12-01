<script>
import { store } from "../store.js";
import CountryFlag from "vue-country-flag-next";

export default {
  name: "AppCardSeries",
  props: {
    infoSeries: Object,
  },
  data() {
    return {
      store,
    };
  },
  components: {
    CountryFlag,
  },
  methods: {
    getFlag(lang) {
      if (lang == "en") {
        console.log(lang);
        return "gb";
      } else {
        return lang;
      }
    },
  },
  computed: {
    vote() {
      return Math.ceil(this.infoSeries.vote_average / 2);
      console.log(this.infoSeries.vote_average);
    },
  },
};
</script>

<template>
  <div class="ms-card text-center" v-if="infoSeries.poster_path">
    <div class="img">
      <img
        :src="`https://image.tmdb.org/t/p/w300/${infoSeries.poster_path}`"
        :alt="infoSeries.name"
      />
    </div>
    <div class="info">
      <div>
        {{ infoSeries.name }}
      </div>
      <div v-if="infoSeries.original_name != infoSeries.name">
        {{ infoSeries.original_name }}
      </div>

      <div>
        <country-flag
          :country="getFlag(infoSeries.original_language)"
          size="normal"
        />
      </div>
      <span v-if="vote != 0">
        <i v-for="n in vote" class="fa-solid fa-star"></i>
        <i v-for="n in 5 - vote" class="fa-regular fa-star"></i>
      </span>
    </div>
  </div>
</template>

<style lang="scss" scoped>
img {
  max-width: 100%;
}
</style>
