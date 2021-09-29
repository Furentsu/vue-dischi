<template>
    <section class="d-flex justify-content-center align-items-center">
        <div class="container my_albums-container">
            <div class="row row-cols-5">
                <div class="col mt-5 mb-5" v-for="album in albumsList" :key="album.title">
                    <Albums />
                </div>
                
            </div>
        </div>
    </section>
  
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

section {
    height: calc(100vh - 70px);
    background-color: $pageBackground;

    .my_albums-container {
        border: 1px solid red;

    }
}
</style>


