<script>
import { store } from "../store.js";
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
};
</script>

<template>
  <div class="card text-center">
    <div class="img">
      <img src="https://via.placeholder.com/300" alt="" />
    </div>
    <h2>{{ info }}</h2>
    <h3>Original title</h3>
    <h4>language</h4>
    <h5>Vote</h5>
  </div>
</template>

<style lang="scss" scoped>
img {
  max-width: 100%;
}
</style>
