<template>
    <section class="d-flex justify-content-center align-items-center">
        <div class="container my_albums-container">
            <div class="row row-cols-5">
                
                <div class="col-12 text-center text-white">
                    <FilteringComp @getGenres='getGenres' :filteredGenres="genresList" />
                </div>

                <div v-for="(album,index) in filteredAlbums" :key="index" class="my_album col mt-5 mb-5">
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
            needle: '',
            filteredAlbums: [],
        }
    },
    methods: {
        getGenres(needle) {
            this.needle = needle;
            this.filteredAlbums = [];
            this.selectedAlbums();
        },

        selectedAlbums() {
            this.albumsList.forEach((item) => {
                if (item.genre == this.needle && !this.filteredAlbums.includes(item)) {
                    this.filteredAlbums.push(item);
                }
             })
        },
    },
    mounted: function() {
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((response) => {
        this.albumsList = [...response.data.response];
        
        this.albumsList.forEach((item) => {
            if (!this.genresList.includes(item.genre)) {
                this.genresList.push(item.genre);
            }
        })

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