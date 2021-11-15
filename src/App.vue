<template>
  <div id="app">
    <SiteHeader />
    <SiteMain />
    <SiteFooter />
  </div>
</template>

<script>
import SiteHeader from "./components/SiteHeader";
import SiteMain from "./components/SiteMain";
import SiteFooter from "./components/SiteFooter";
import axios from "axios";

export default {
  name: "App",
  components: {
    SiteHeader,
    SiteMain,
    SiteFooter,
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((r) => {
        console.log(r);
      })
      .catch((e) => {
        console.log(e, "OPS!");
      });
  },
};
</script>

<style lang="scss">
@import "./node_modules/bootstrap/scss/bootstrap.scss";
</style>
