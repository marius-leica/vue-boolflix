<template>
  <div id="app">
    <TheHeader @searchChanged="search"></TheHeader>

    <TheMain :userInput="searchText"></TheMain>

  </div>
</template>

<script>
// import axios from "axios";
import TheHeader from "./components/TheHeader.vue";
import TheMain from "./components/TheMain.vue";

export default {
  name: "App",
  components: {
    TheHeader,
    TheMain,
  },
  data() {
    return {
      searchText: "",
    };
  },
  methods: {
    search(searchText) {
      this.searchText = searchText;
    },


  }
};
</script>

<style lang="scss" scoped>
@import "assets/scss/main.scss";
</style>
