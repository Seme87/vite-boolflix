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
  <nav class="navbar bg-light">
    <div class="container-fluid">
      <form class="d-flex" role="search" @submit.prevent="">
        <input
          @click="$emit('cliccato')"
          class="form-control me-2"
          type="search"
          placeholder="Search"
          aria-label="Search"
        />
        <button class="btn btn-outline-success" type="submit">Search</button>
      </form>
    </div>
  </nav>
</template>

<style lang="scss" scoped>
h1 {
  color: green;
}
</style>
