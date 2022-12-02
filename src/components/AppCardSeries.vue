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

  <div class="ms-card " v-if="infoSeries.poster_path">

    <div class="img">

      <img :src="`https://image.tmdb.org/t/p/w342/${infoSeries.poster_path}`" :alt="infoSeries.name"/>

      <div class="info">

        <div class="ms-title">
          <strong>Titolo:</strong>{{ infoSeries.name }}
        </div>

        <div class="ms-original-title" v-if= "infoSeries.original_name != infoSeries.name">
          <strong>Titolo originale:</strong>
        {{ infoSeries.original_name }}
        </div>

        <!-- <div>
          <country-flag :country="getFlag(info.original_language)" size="normal" />
        </div> -->

        <div class="ms-overview">
          <strong>Overview:</strong>
          {{ infoSeries.overview }}
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
