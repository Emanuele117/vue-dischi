<template>
  <form action="">
    <label for="musics">Choose a genre: </label>
    <select
      name="genre"
      id="musics"
      v-model="genreSearch"
      @change.prevent="$emit('select-genre', genreSearch)"
    >
      <option value="">All</option>
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
      genreSearch: "",
    };
  },
};
</script>

<style lang="scss">
label {
  color: white;
  margin: 5px;
  margin-left: 35rem;
  margin-top: 1rem;
}
</style>