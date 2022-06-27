<template>
    <div>
        <select @change="selectedGenre(genreSelected)" v-model="genreSelected" class="form-select" aria-label="Default select example">
            <option selected>Select genres</option>
            <option v-for="(genre, i) in selectorInfo" :key="i" :value="genre"> {{ genre }} </option>
        </select>
    </div>
</template>

<script>
export default {
    data() {
        return {
            selected: '',
            genreSelected: '',
        };
    },
    props: {
        selectorInfo: Array
    },
    methods: {
        selectedGenre(genreSelected) {
            console.log(genreSelected)
        }
        }
}
</script>

<style>
</style>