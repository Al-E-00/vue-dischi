<template>
    <div>
        <div class="bg-dark">
            <div class="alert alert-info">
                Current Genre: {{searchGenre}}
            </div>
            <div class="container custom-container">
                <div class="row row-cols-5 custom-album-view">
                    <div class="col" v-for="album in filteredAlbums" :key="album.title">
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
    props: {
        searchGenre: String
    },
    name: 'AlbumsList',
    components: { MainAlbum },
    data() {
        return {
            apiURL: 'https://flynn.boolean.careers/exercises/api/array/music',
            albumsList: [],
            loading: true,
        };
    },
    computed: {
        filteredAlbums() {
            if(!this.searchGenre){
                return this.albumsList;
            }
            return this.albumsList.filter((album) =>{
                return album.genre == this.searchGenre
            })
        }
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