<template>
    <div>
        <div class="bg-dark">
            <div class="container custom-container">
                <div class="row row-cols-5 custom-album-view">
                    <div class="col" v-show="currentGenre" v-for="album in albumsList" :key="album.title" @search="changeGenre">
                        <MainAlbum :info="album"></MainAlbum>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import MainAlbum from './MainAlbum.vue';


export default {
    name: 'AlbumsList',
    components: { MainAlbum },
    data() {
        return {
            apiURL: 'https://flynn.boolean.careers/exercises/api/array/music',
            albumsList: [],
            loading: true,
            currentGenre: 'Select',
        };
    },
    methods: {
        fetchAlbumsList() {
            axios
                .get(this.apiURL)
                .then((resp) => {
                    this.albumsList = resp.data.response;
                });
        },
        changeGenre(newGenre) {
            this.currentGenre = newGenre;
        }
    },

    mounted() {
        this.fetchAlbumsList();
    }
};
</script>

<style lang="scss" scoped>
.custom-container {
    width: 60%;
    padding: 2rem 0;
}
</style>