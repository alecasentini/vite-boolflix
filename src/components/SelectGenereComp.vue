<script>
import axios from 'axios';
import { store } from '../store';

export default {
    name: "SelectGenereComp",
    data() {
        return {
            store,
            genres: [],
            selectedGenre: '',
            moviesGenres: [28, 12, 16, 35, 80, 99, 18, 10751, 14, 36, 27, 10402, 9648, 10749, 878, 10770, 53, 10752, 37],
            seriesGenres: [10759, 16, 35, 80, 99, 18, 10751, 10762, 9648, 10763, 10764, 10765, 10766, 10767, 10768, 37]
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
    <select class="form-select" aria-label="Default select example" v-model="selectedGenre" @change="selectChange">
        <option selected value="">Seleziona Genere</option>
        <option v-for="genre in genres" :value="genre.id">
            {{ genre.name }}
            {{ moviesGenres.includes(genre.id) && seriesGenres.includes(genre.id) ? ' (Film - Serie TV)' : '' }}
            {{ moviesGenres.includes(genre.id) && !seriesGenres.includes(genre.id) ? ' (Film)' : '' }}
            {{ !moviesGenres.includes(genre.id) && seriesGenres.includes(genre.id) ? ' (Serie TV)' : '' }}
        </option>
    </select>
</template>

<style lang="scss">
select {
    width: 270px !important;
}
</style>
