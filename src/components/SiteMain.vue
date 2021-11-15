<template>
  <div class="container">
    <div class="row">
      <div class="col-md-3" v-for="response in responses" :key="response.id">
        <div class="music">
          <img :src="response.poster" :alt="response.genre" />
          <h3>{{ response.title }}</h3>
          <p>{{ response.author }}</p>
          <p>{{ response.year }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      responses: [],
    };
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((r) => {
        console.log(r.data);
        this.responses = r.data;
      })
      .catch((e) => {
        console.log(e, "OPS");
      });
  },
};
</script>

<style>
</style>