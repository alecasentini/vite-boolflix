<script >
import { store } from '../store.js'
export default {
    name: "MoviesCardComp",
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
    <div class="card" v-for="movie in store.movies" :key="movie.id">
        <img :src="'https://image.tmdb.org/t/p/w342/' + movie.poster_path"
            onerror="this.onerror=null;this.src='../../public/img/image_null.png';" />
        <div class="card-body">
            <h5 class="card-title">{{ movie.title }}</h5>
            <h6 class="card-subtitle mb-2" v-if="movie.original_title !== movie.title">{{ movie.original_title }}
            </h6>
            <img :src="`https://flagcdn.com/h20/${movie.original_language === 'ja' ? 'jp' : (movie.original_language === 'en' ? 'gb' : (movie.original_language === 'ko' ? 'kr' : movie.original_language))}.png`"
                onerror="this.onerror=null;this.src='../../public/img/pirate_flag.jpg';">

            <p class="card-text">
                Voto:
                <font-awesome-icon v-for="star in Math.ceil(movie.vote_average / 2)" :key="star" :icon="['fas', 'star']" />
                <font-awesome-icon v-for="star in 5 - Math.ceil(movie.vote_average / 2)" :key="star"
                    :icon="['far', 'star']" />
            </p>
            <p class="card-text trama">
                <span class="fw-bolder">Trama:</span>
                {{ movie.overview.length > 300 ? movie.overview.slice(0, 300) + '...' : movie.overview }}
            </p>
            <p class="card-text d-inline mx-2" v-for="genre in movie.genre_ids" :key="genre">{{ genre }}</p>
        </div>
    </div>
</template>

<style lang="scss">
.card {
    min-width: calc(100% / 5 - 10px) !important;
    height: 350px !important;
    margin: 10px 5px;
    border: 0 !important;
    position: relative;
    overflow: hidden;
    cursor: default;
    border-radius: 0 !important;

    img {
        height: 100%;
        object-fit: fill;
    }

    .card-body {
        position: absolute;
        background-color: rgba(0, 0, 0, 0.8);
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

        .fa-star {
            color: yellow;
        }

        .trama {
            font-size: 10px;
        }


    }

    &:hover .card-body {
        display: block;
    }
}
</style>