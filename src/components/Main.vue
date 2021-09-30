<template>
    <section class="d-flex justify-content-center align-items-center">
        <div class="container my_albums-container">
            <div class="row row-cols-5">
                <div v-for="album in albumsList" :key="album.id" class="my_album col mt-5 mb-5">
                    <Albums :entireAlbum="album"/>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
import axios from 'axios';
import Albums from './Albums.vue'


export default {
    name: 'Main',
    components: {
        Albums,
    },
    data: function() {
    return {
            albumsList: [],
        }
  },
    mounted: function() {
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((response) => {
        this.albumsList = [...response.data.response];
        console.log(this.albumsList)
    })
  }
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

section {
    background-color: $pageBackground;

}

</style>