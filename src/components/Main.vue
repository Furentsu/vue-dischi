<template>
  <div>
      <Albums />
  </div>
</template>

<script>
import Albums from '../components/Albums.vue'

export default {
    name: 'Main',
    components: {
        Albums,
    }
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';


</style>