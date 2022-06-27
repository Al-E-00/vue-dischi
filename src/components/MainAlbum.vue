<template>
    <div>
        <div class="card-container-custom">
            <div class="card-img-container">
                <img :src="info.poster" :alt="info.title">
            </div>
            <div class="card-body-custom">
                <h5 class="card-title-custom"> {{ info.title }} </h5>
                <p class="card-custom-text author">{{ info.author}} </p>
                <p class="card-custom-text year">{{ info.year }} </p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'MainAlbum',
    props: {
        info: Object,
    }
}
</script>


<style lang="scss" scoped>
@import './scss/albumStyle.scss';
</style>