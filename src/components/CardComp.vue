<script >
import { store } from '../store.js'
export default {
    name: "CardComp",
    data() {
        return {
            store
        }
    }
}
</script>

<template>
    <div class="card" v-for="movie in store.movies" :key="movie.id">
        <img :src="'https://image.tmdb.org/t/p/w342/' + movie.poster_path" />
        <div class="card-body">
            <h5 class="card-title">{{ movie.title }}</h5>
            <h6 class="card-subtitle mb-2">{{ movie.original_title }}</h6>
            <img
                :src="`https://flagcdn.com/h20/${movie.original_language === 'ja' ? 'jp' : (movie.original_language === 'en' ? 'gb' : movie.original_language)}.png`">
            <p class="card-text">Voto {{ movie.vote_average }}</p>
        </div>
    </div>
</template>

<style lang="scss">
.card {
    width: calc(100% / 5 - 10px);
    height: 300px !important;
    margin: 10px 5px;
    border: 0 !important;
    position: relative;

    img {
        height: 100%;
        object-fit: fill;
    }

    .card-body {
        position: absolute;
        background-color: black;
        height: 100%;
        width: 100%;
        display: none;

        h5 {
            color: white;
        }

        h6 {
            color: lightgrey;
        }

        p {
            color: white;
        }


        img {
            height: 20px;
            width: 30px;
        }


    }

    &:hover .card-body {
        display: block;
    }
}
</style>