<script >
import axios from 'axios'
import { store } from '../store.js'

export default {
    name: "SearchbarComp",
    data() {
        return {
            searchQuery: '',
        };
    },

    methods: {
        search() {

            axios.get(`https://api.themoviedb.org/3/search/movie?api_key=1fb3006bd468938300e6513240f07c00&language=it&query=${this.searchQuery}`)
                .then(res => {
                    store.movies = res.data.results
                    console.log(res.data.results)
                })
        },
    }
}

</script>

<template>
    <div class="d-flex flex-wrap">

        <input type="text" v-model="searchQuery" class="me-3 ps-2" @keyup.enter="search">
        <button type="button" class="btn btn-danger" @click="search">Search</button>

    </div>
</template>

<style lang="scss"></style>