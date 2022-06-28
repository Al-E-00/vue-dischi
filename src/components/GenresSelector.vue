<template>
    <div>
        <select @change="selectedGenre(genreSelected)" v-model="genreSelected" class="form-select" aria-label="Default select example">
            <option v-for="(genre, i) in genresList" :key="i" :value="genre"> {{ genre }} </option>
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
        genresList: Array
    },
    methods: {
        selectedGenre(genreSelected) {
            this.$emit('changeGenre', genreSelected);
            this.genreSelected = genreSelected;
            console.log(this.genreSelected);
        }
        }
}
</script>

<style>
</style>