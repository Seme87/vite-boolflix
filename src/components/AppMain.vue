<script>
import { store } from "../store.js";

export default {
  name: "AppMain",
  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <div>
    <h2>Main</h2>
  </div>
</template>

<style lang="scss" scoped>
h2 {
  color: gold;
}
</style>
