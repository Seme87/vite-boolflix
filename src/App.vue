<script>
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
export default {
  components: {
    AppHeader,
    AppMain,
  },
  methods: {
    saluta() {
      console.log("Buongiorno");
    },
  },
};
</script>

<template>
  <div>
    <AppHeader @cliccato="saluta" />
    <AppMain />
  </div>
</template>

<style lang="scss">
@import "./style/global.scss";
</style>
