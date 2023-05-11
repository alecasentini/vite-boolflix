<script>
import axios from 'axios';
import { store } from '../store';

export default {
    name: "SelectGenereComp",
    data() {
        return {
            store,
            genres: [],
            selectedGenre: ''
        }
    },
    created() {
        axios.get('https://api.themoviedb.org/3/genre/movie/list?api_key=1fb3006bd468938300e6513240f07c00&language=it')
            .then(res => {
                for (let i = 0; i < res.data.genres.length; i++) {
                    const genre = res.data.genres[i];
                    if (!this.genres.find(g => g.id === genre.id)) {
                        this.genres.push(genre);
                    }
                }
            }),
            axios.get('https://api.themoviedb.org/3/genre/tv/list?api_key=1fb3006bd468938300e6513240f07c00&language=it')
                .then(res => {
                    for (let i = 0; i < res.data.genres.length; i++) {
                        const genre = res.data.genres[i];
                        if (!this.genres.find(g => g.id === genre.id)) {
                            this.genres.push(genre);
                        }
                    }
                })
    },

    methods: {
        selectChange() {
            axios.get(`https://api.themoviedb.org/3/discover/movie?api_key=1fb3006bd468938300e6513240f07c00&language=it&sort_by=popularity.desc&include_adult=false&include_video=false&page=1&with_genres=${this.selectedGenre}`)
                .then(res => {
                    this.store.movies = res.data.results
                }),
                axios.get(`https://api.themoviedb.org/3/discover/tv?api_key=1fb3006bd468938300e6513240f07c00&language=it&sort_by=popularity.desc&include_adult=false&include_video=false&page=1&with_genres=${this.selectedGenre}`)
                    .then(res => {
                        this.store.series = res.data.results
                    })
        }

    }
}

</script>

<template>
    <select class="form-select" aria-label="Default select example" v-model="this.selectedGenre" @change="selectChange">
        <option selected value="">Seleziona Genere</option>
        <option v-for="genre in genres" :value="genre.id">{{ genre.name }}</option>
    </select>
</template>

<style lang="scss">
select {
    width: 180px !important;
}
</style>
