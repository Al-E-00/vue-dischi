<template>
    <div>
        <nav class="navbar-custom bg-secondary d-flex align-items-center">
            <a class="navbar-brand" href="#">
                <div class="container">
                    <img src="https://brandlogos.net/wp-content/uploads/2021/12/spotify-brandlogo.net_.png" alt=""
                        width="40" height="40">
                </div>
            </a>
            <GenresSelector :genres-list="genresList" @searchGenre="$emit('searchGenre', $event)"/>
        </nav>
    </div>
</template>

<script>
import axios from 'axios';
import GenresSelector from './GenresSelector.vue';

export default {
    name: "theHeader",
    components: { GenresSelector },
    props: {
        genresList: Array
    },
    data() {
        return {
            selectorInfo: [],
            currentGenres: 'Select',
        };
    },
    methods: {
        fetchSelectorInfo() {
            axios
                .get("https://flynn.boolean.careers/exercises/api/array/music", {
                    params: {
                        genre: this.currentGenres
                    }
                })
                .then((resp) => {
                    for(let i = 0; i < resp.data.response.length; i++) {
                        if (this.selectorInfo.includes(resp.data.response[i].genre) === false) {
                            this.selectorInfo.push(resp.data.response[i].genre);
                            }
                        console.log(this.selectorInfo)
                    }
            });
        },
        onChangePage(newGenre) {
            this.currentGenres = newGenre;
            this.fetchSelectorInfo();
        }
    },
    mounted() {
        this.fetchSelectorInfo();
    },
}
</script>

<style lang="scss">
@import "./scss/theHeader.scss";
</style>