<script >
import { store } from '../store.js'
export default {
    name: "SeriesCardComp",
    data() {
        return {
            store
        }
    },
    methods: {
        mapVote(vote) {
            const roundedVote = Math.round(vote)
            const mappedVote = Math.ceil(roundedVote / 2)
            return mappedVote
        }
    }
}
</script>

<template>
    <div class="card" v-for="serie in store.series" :key="serie.id">
        <img :src="'https://image.tmdb.org/t/p/w342/' + serie.poster_path"
            onerror="this.onerror=null;this.src='../../public/img/image_null.png';" />
        <div class="card-body">
            <h5 class="card-title">{{ serie.name }}</h5>
            <h6 class="card-subtitle mb-2">{{ serie.original_name }}</h6>
            <img
                :src="`https://flagcdn.com/h20/${serie.original_language === 'ja' ? 'jp' : (serie.original_language === 'en' ? 'gb' : serie.original_language)}.png`">
            <p class="card-text">Voto {{ mapVote(serie.vote_average) }}</p>
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