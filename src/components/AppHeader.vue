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
  <header class="d-flex mb-3">
    <div class="logo">
      <img src="https://via.placeholder.com/140x100" alt="logo" />
    </div>
    <nav class="navbar">
      <div class="container-fluid">
        <form class="d-flex" role="search" @submit.prevent="">
          <input
            v-model="store.searchText"
            class="form-control me-2"
            type="search"
            placeholder="Search"
            aria-label="Search"
          />
          <button
            class="btn btn-outline-success"
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
  justify-content: space-between;
  background-color: rgba(0, 0, 0, 0.8);
  height: 80px;
  padding: 15px 10px;

  .logo {
    img {
      width: 100%;
      height: 100%;
    }
  }
}
</style>
