<template>
  <div class="album-item">
      <img class="image-fluid" :src="poster"> 
      <h3>{{name}}</h3>
      <h4>{{author}}</h4>
      <h5>{{year}}</h5>
  </div>
</template>

<script>


export default {
  name: 'Albums',
  props: ['name', 'author', 'year', 'poster'],
}

</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

.album-item {
  border: 1px solid red;
  background-color: $headerCardBackground;
  color: white;
  text-align: center;

  height: 330px;

  img {
    width: 80%;
  }
}
</style>