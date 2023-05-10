<script >
import MoviesCardComp from './MoviesCardComp.vue';
import SeriesCardComp from './SeriesCardComp.vue';
import { store } from '../store'

export default {
    name: "SearchResultComp",
    components: {
        MoviesCardComp,
        SeriesCardComp
    },
    data() {
        return {
            store
        }
    }

}
</script>

<template>
    <div class="container h-100 d-flex flex-column p-0 pb-2">

        <h2 class="text-white fw-bolder my-1">Film</h2>

        <div class="d-flex overflow-x-scroll p-0 my-2">

            <MoviesCardComp />
            <div v-if="!store.movies.length" class="mt-4 text-white fw-bolder">Nessun film trovato</div>
        </div>

        <h2 class="text-white fw-bolder my-1">Serie TV</h2>

        <div class=" d-flex flex-nowrap overflow-x-scroll p-0 pb-2 my-2">

            <SeriesCardComp />
            <div v-if="!store.series.length" class="mt-4 text-white fw-bolder">Nessuna serie trovata</div>
        </div>

    </div>
</template>


<style lang="scss"></style>