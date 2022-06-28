<template>
  <div id="app">
    <Header :genres-list ="genresList" @searchGenre="onSearchGenre"/>
    <Albums @genresUpdated="onGenresUpdate" :search-genre="searchGenre"/>
  </div>
</template>

<script>
import Header from './components/TheHeader.vue';
import Albums from './components/AlbumList.vue';

export default {
    components: { Header, Albums },
    data() {
      return{
        genresList: [],
        searchGenre: ""
      };
    },
    methods: {
      onGenresUpdate(genresList) {
        this.genresList = genresList
      },
      onSearchGenre(genre) {
        this.searchGenre = genre
      }
    }
}
</script>

<style lang="scss">
@import "./components/scss/custom_variables.scss";
@import "~bootstrap/scss/bootstrap";

</style>
