<script>
import axios from 'axios';
import { store } from '../store';

export default {
    name: "SelectGenereComp",
    data() {
        return {
            store,
            genres: [],
        }
    },
    created() {
        axios.get('https://api.themoviedb.org/3/genre/movie/list?api_key=1fb3006bd468938300e6513240f07c00&language=it')
            .then(res => {
                for (let i = 0; i < res.data.genres.length; i++) {
                    this.genres.push(res.data.genres[i].name);
                    console.log(res.data.genres[i].name)
                }
            })
    },
    methods: {
        selectChange() {

        }
    }
}
</script>

<template>
    <select class="form-select" aria-label="Default select example">
        <option selected>Seleziona Genere</option>
        <option v-for="genre in genres" :value="genre.id">{{ genre }}</option>
    </select>
</template>

<style lang="scss">
select {
    width: 180px !important;
}
</style>
