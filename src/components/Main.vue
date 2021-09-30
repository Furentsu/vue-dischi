<template>
    <section class="d-flex justify-content-center align-items-center">
        <div class="container my_albums-container">
            <div class="row row-cols-5">
                <div class="my_album col mt-5 mb-5" v-for="album in albumsList" :key="album.id">
                    <Albums :name="album.title" :author="album.author" :year="album.year" :poster="album.poster"/>
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
    height: calc(100vh - 70px);
    background-color: $pageBackground;

}

</style>