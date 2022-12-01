<script>
import { store } from "../store.js";
import CountryFlag from "vue-country-flag-next";

export default {
  name: "AppCardMovie",
  props: {
    info: Object,
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
      return Math.ceil(this.info.vote_average / 2);
    },
  },
};
</script>

<template>
  <div class="ms-card text-center" v-if="info.poster_path">
    <div class="img">
      <img
        :src="`https://image.tmdb.org/t/p/w342/${info.poster_path}`"
        :alt="info.title"
      />
    </div>
    <div class="info">
      <div>
        {{ info.title }}
      </div>
      <div v-if="info.original_title != info.title">
        {{ info.original_title }}
      </div>

      <div>
        <country-flag
          :country="getFlag(info.original_language)"
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
