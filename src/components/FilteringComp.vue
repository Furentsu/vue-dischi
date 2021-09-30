<template>
  <div>
    <select>
        <option v-for="genre in filteredGenres" :key="genre"> {{genre}} </option>
    </select>
  </div>
</template>

<script>
export default {
    name: 'FilteringComp',
    props: ['filteredGenres'],
    data: function() {
        return {

        }
    },
    methods: {

    },

}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

</style>