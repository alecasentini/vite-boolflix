<script >
import MoviesCardComp from './MoviesCardComp.vue';
import SeriesCardComp from './SeriesCardComp.vue';

export default {
    name: "SearchResultComp",
    components: {
        MoviesCardComp,
        SeriesCardComp
    },

}
</script>

<template>
    <div class="container h-100 d-flex flex-wrap p-0">
        <MoviesCardComp />
        <SeriesCardComp />
    </div>
</template>

<style lang="scss"></style>