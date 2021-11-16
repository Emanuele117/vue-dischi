<template>
  <form action="">
    <label for="musics">Choose a genre: </label>
    <select
      name="musics"
      id="musics"
      v-model="filter"
      @change.prevent="$emit('select-music', filter)"
    >
      <option value="Rock">Rock</option>
      <option value="Pop">Pop</option>
      <option value="Jazz">Jazz</option>
      <option value="Metal">Metal</option>
    </select>
  </form>
</template>

<script>
export default {};
</script>

<style>
</style>