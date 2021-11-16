<template>
  <form action="">
    <label for="musics">Choose a genre: </label>
    <select
      name="musics"
      id="musics"
      v-model="select"
      @change.prevent="$emit('select', select)"
    >
      <option value="all">All</option>
      <option value="genre" v-for="(genre, index) in genres" :key="index">
        {{ genre }}
      </option>
    </select>
  </form>
</template>

<script>
export default {
  name: "selectMusic",
  props: {
    genres: [],
  },
  data() {
    return {
      select: "",
    };
  },
};
</script>

<style>
</style>