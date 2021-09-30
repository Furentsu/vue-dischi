<template>
  <div class="album-item">
      <div class="image-container">
        <img :src="entireAlbum.poster" :alt="entireAlbum.title"> 
      </div>
      <h3>{{entireAlbum.name}}</h3>
      <h2>{{entireAlbum.title}}</h2>
      <h4>{{entireAlbum.author}}</h4>
      <h5>{{entireAlbum.year}}</h5>
  </div>
</template>

<script>


export default {
  name: 'Albums',
  props: ['entireAlbum'],
}

</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

.album-item {
  background-color: $headerCardBackground;
  color: white;
  text-align: center;

  min-height: 400px;

  .image-container {
    width: 100%;

    img {
      width: 80%;
    }
  }
}
</style>