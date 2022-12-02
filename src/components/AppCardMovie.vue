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

  <div class="ms-card " v-if="info.poster_path">

    <div class="img">

      <img :src="`https://image.tmdb.org/t/p/w342/${info.poster_path}`" :alt="info.title"/>

      <div class="info">

        <div class="ms-title">
          <strong>Titolo:</strong>{{ info.title }}
        </div>

        <div class="ms-original-title" v-if="info.original_title != info.title">
          <strong>Titolo originale:</strong>
        {{ info.original_title }}
        </div>

        <!-- <div>
          <country-flag :country="getFlag(info.original_language)" size="normal" />
        </div> -->

        <div class="ms-overview">
          <strong>Overview:</strong>
          {{ info.overview }}
        </div>

        <div class="ms-vote" v-if="vote != 0">
          <strong>Voto:</strong> 
          <i v-for="n in vote" class="fa-solid fa-star"></i>
          <i v-for="n in 5 - vote" class="fa-regular fa-star"></i>
        </div>

      </div>

    </div>

    

  </div>

</template>

<style lang="scss" scoped>

.ms-card{
  aspect-ratio: 3/4;
  

}
.info{
  padding: 10px;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  display: none;
  color: white;
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  background-color: rgba(0, 0, 0, 0.587);
  transition:all  2s ease-in-out;
  overflow-y: scroll;
}
.img {
  position: relative;
  width: 100%;
  aspect-ratio: 3/4;
  
}

.ms-card:hover .info{
  display: block;
}




img {
  width: 100%;
  display: block;
  
}

.ms-overview{
  font-size: 13px;
  padding: 10px 0;
}

.ms-original-title{
  font-size: 12px;
}
.ms-title {
  font-size: 15px;
}
.ms-vote{
  font-size: 14px;
  i{
    padding-left: 5px;
    color: gold;
  }
}

</style>
