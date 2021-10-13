<template>
  <div class="selection_bar">
    <select v-model="needle" @change="$emit('getGenres', needle)">
      <option value="" disabled selected hidden>Choose a genre</option>
      <option v-for="(genre,index) in filteredGenres" :key="index"> {{genre}} </option>
    </select>
  </div>
</template>

<script>
export default {
    name: 'FilteringComp',
    props: ['filteredGenres'],
    data: function() {
        return {
          needle: "",
        }
    },
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

.selection_bar {
  position: absolute;
  top: 100px;
  left: 50%;
  transform: translate(-50%);
}

</style>