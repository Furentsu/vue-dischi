<template>
  <div class="album-item">
      <!-- <img src="" alt=""> -->
      <h3>Titolo</h3>
      <h4>Artista</h4>
      <h5>Data</h5>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Albums',
  data: function() {
  return {
    albumsList: [],
  }
  },
  mounted: function() {
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then((response) => {
      console.log(response.data.response)
      this.albumsList = [...response.data.response];
    })
  }
}

</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

.album-item {
  border: 1px solid red;
  color: white;

  width: 100%;
  height: 300px;
}
</style>