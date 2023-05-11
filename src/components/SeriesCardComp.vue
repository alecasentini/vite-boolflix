<script >
import { store } from '../store.js'
import axios from 'axios'
export default {
    name: "SeriesCardComp",
    data() {
        return {
            store,
            genres: []
        }
    },
    methods: {
        mapVote(vote) {
            const roundedVote = Math.round(vote)
            const mappedVote = Math.ceil(roundedVote / 2)
            return mappedVote
        },
        getGenreNameById(id) {
            const genre = this.genres.find(genre => genre.id === id);
            return genre ? genre.name : '';
        }
    },
    created() {
        axios.get('https://api.themoviedb.org/3/genre/tv/list?api_key=1fb3006bd468938300e6513240f07c00&language=it')
            .then(res => {
                this.genres = res.data.genres;
                console.log(res.data.genres)
            })
    }
}
</script>

<template>
    <div class="card" v-for="serie in store.series" :key="serie.id">
        <img :src="'https://image.tmdb.org/t/p/w342/' + serie.poster_path"
            onerror="this.onerror=null;this.src='../../public/img/image_null.png';" />
        <div class="card-body">
            <h5 class="card-title">{{ serie.name }}</h5>
            <h6 class="card-subtitle mb-2" v-if="serie.original_name !== serie.name">{{ serie.original_name }}</h6>
            <img :src="`https://flagcdn.com/h20/${serie.original_language === 'ja' ? 'jp' : (serie.original_language === 'en' ? 'gb' : (serie.original_language === 'ko' ? 'kr' : serie.original_language))}.png`"
                onerror="this.onerror=null;this.src='../../public/img/pirate_flag.jpg';">
            <p class="card-text">
                Voto:
                <font-awesome-icon v-for="star in Math.ceil(serie.vote_average / 2)" :key="star" :icon="['fas', 'star']" />
                <font-awesome-icon v-for="star in 5 - Math.ceil(serie.vote_average / 2)" :key="star"
                    :icon="['far', 'star']" />
            </p>
            <p class="card-text trama">
                Trama: {{ serie.overview.length > 300 ? serie.overview.slice(0, 300) + '...' : serie.overview }}
            </p>
            <p class="genere card-text d-inline me-1" v-for="genreId in serie.genre_ids" :key="genreId">
                {{ getGenreNameById(genreId) }}
            </p>
        </div>
    </div>
</template>

<style lang="scss"></style>