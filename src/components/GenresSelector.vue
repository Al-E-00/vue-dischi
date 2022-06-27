<template>
    <div>
        <select v-model="genreSelected" class="form-select" aria-label="Default select example">
            <option selected>Select genres</option>
            <option v-for="(genre, i) in selectorInfo" :key="i" :value="genre"
                @click="selectedGenre(genre)"> {{ genre }} </option>
        </select>
    </div>
</template>

<script>
export default {
    data() {
        return {
            genreSelected: '',
        };
    },
    props: {
        selectorInfo: Array
    },
    methods: {
        selectedGenre(selected) {
            console.log(selected);
        }
    }
}
</script>

<style>
</style>