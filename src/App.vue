<template>
  <div id="app">
    <Header />
    <Albums />
  </div>
</template>

<script>
import Header from './components/TheHeader.vue';
import Albums from './components/AlbumList.vue';

export default {
    components: { Header, Albums }
}
</script>

<style lang="scss">
@import "./components/scss/custom_variables.scss";
@import "~bootstrap/scss/bootstrap";

</style>
