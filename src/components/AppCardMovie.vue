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
  <div class="ms-card text-center">
    <div class="img">
      <img src="https://via.placeholder.com/300" alt="" />
    </div>
    <div class="info">
      <div>
        {{ info.title }}
      </div>
      <div>
        {{ info.original_title }}
      </div>
      <div>
        {{ info.original_language }}
      </div>
      <div>
        {{ info.vote_average }}
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
img {
  max-width: 100%;
}
</style>
