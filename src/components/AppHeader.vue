<script>
import { store } from "../store";

export default {
  name: "AppHeader",
  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <header class="d-flex ">

    <div class=" logo ">
      <img src="https://image.tmdb.org/t/p/w300/wwemzKWzjKYJFfCeiB57q3r4Bcm.png" alt="logo" />
    </div>

    <div class="point-bar d-flex">
      <ul class="d-flex">
        <li class="px-2"><a href="#">Home</a></li>
        <li><a href="#">Serie Tv</a></li>
        <li><a href="#">Film</a></li>
        <li><a href="#">Originali</a></li>
        <li><a href="#">Aggiunti di recente</a></li>
        <li><a href="#">La mia lista</a></li>
      </ul>
    </div>

    <nav class="ms-navbar ">
      <div class="">
        <form class="d-flex" role="search" @submit.prevent="">
          <input
            v-model="store.searchText"
            class="px-2 py-1 me-2"
            type="search"
            placeholder="Search"
            aria-label="Search"
          />
          <button
            class="btn "
            @click="$emit('performSearch')"
            type="submit"
          >
            Search
          </button>
        </form>
      </div>
    </nav>

  </header>
</template>

<style lang="scss" scoped>
header {
 
  background-color: #1a130d;
  // filter: brightness(0.4);
  height: 80px;
  padding: 10px 10px;

  .logo {
    width: 10%;
   padding: 10px;
    img {
      width: 100%;
      height: 100%;
      display: block;
    }
  }
  .point-bar{
    align-items: center;
    padding: 10px;
    width: 50%;
  }

  ul{
    align-items: center;
    margin-top: 0; 
    margin-bottom: 0;
    padding: 0;
    li{
      padding: 0 8px;
      list-style: none;
      a{
        color: white;
        text-decoration: none;
        color: gray;
      }
    }
  }

  li:hover a{
    color: white;
  }

  .ms-navbar{
    flex-grow: 1;
    padding: 0 10px;
    align-items: center;
    display: flex;
    justify-content: flex-end;
  }


  input{
    border-radius: 10px;
    border: none;
    
  }

  .btn{
    padding: 0px 20px;
    color: white;
    background-color: red;
  }
}
</style>
