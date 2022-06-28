<template>
    <div>
        <div class="bg-dark">
            <div class="container custom-container">
                <div class="row row-cols-5 custom-album-view">
                    <div class="col" v-for="album in albumsList" :key="album.title">
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
    props: {
        changeGenre: String
    },
    data() {
        return {
            apiURL: 'https://flynn.boolean.careers/exercises/api/array/music',
            albumsList: [],
            newAlbumsList: [],
            loading: true,
        };
    },
    methods: {
        fetchAlbumsList() {
            axios
                .get(this.apiURL)
                .then((resp) => {
                    this.albumsList = resp.data.response;

                    this.$emit("genresUpdated", this.genresList())
                })
                .catch(() => {
                    alert("Due to a problem, the operation has fallen through")
                })
        },
        genresList() {
            const list = [];

            this.albumsList.forEach( album => {
                if(!list.includes(album.genre)) {
                    list.push(album.genre)
                }
            })

            return list;
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