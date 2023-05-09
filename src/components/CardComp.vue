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
        <div class="card-body">
            <h5 class="card-title">{{ movie.title }}</h5>
            <h6 class="card-subtitle mb-2 text-muted">{{ movie.original_title }}</h6>
            <img :src="`https://flagcdn.com/h20/${movie.original_language}.png`">
            <p class="card-text">{{ movie.vote_average }}</p>
        </div>
    </div>
</template>

<style lang="scss">
.card {
    width: calc(100% / 5 - 10px);
    height: 250px !important;
    margin: 10px 5px;
}
</style>