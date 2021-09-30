<template>
    <section class="d-flex justify-content-center align-items-center">
        <div class="container my_albums-container">
            <div class="row row-cols-5">
                
                <div class="col-12 text-center text-white">
                    <FilteringComp :filteredGenres="genresList" />
                </div>

                <div v-for="album in albumsList" :key="album.id" class="my_album col mt-5 mb-5">
                    <Albums :entireAlbum="album"/>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
import axios from 'axios';
import Albums from './Albums.vue';
import FilteringComp from './FilteringComp.vue';


export default {
    name: 'Main',
    components: {
        Albums,
        FilteringComp,
    },
    data: function() {
    return {
            albumsList: [],
            genresList: [],
        }
  },
    mounted: function() {
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((response) => {
        this.albumsList = [...response.data.response];
        
        this.albumsList.forEach((item) => {
            if (!this.genresList.includes(item.genre)) {
                this.genresList.push(item.genre)
            }
        })
        console.log(this.albumsList)
        console.log(this.genresList)
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