<template>
  <div id="app">
    <Header :genres-list ="genresList"/>
    <Albums @genresUpdated="onGenresUpdate"/>
  </div>
</template>

<script>
import Header from './components/TheHeader.vue';
import Albums from './components/AlbumList.vue';

export default {
    components: { Header, Albums },
    props: {
        changeGenre: String
    },
    data() {
      return{
        genresList: []
      };
    },
    methods: {
      onGenresUpdate(genresList) {
        this.genresList = genresList
      }
    }
}
</script>

<style lang="scss">
@import "./components/scss/custom_variables.scss";
@import "~bootstrap/scss/bootstrap";

</style>
