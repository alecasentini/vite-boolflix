<script >
import HeaderComp from './components/HeaderComp.vue'
import MainComp from './components/MainComp.vue';
import { store } from './store'
import axios from 'axios'

export default {
  name: "App",
  components: {
    HeaderComp,
    MainComp
  },
  data() {
    return {
      store
    }
  },
  created() {
    axios.get(`https://api.themoviedb.org/3/movie/popular?api_key=1fb3006bd468938300e6513240f07c00&language=it&page=1`)
      .then(res => {
        store.movies = res.data.results
        console.log(res.data.results)
      }),
      axios.get(`https://api.themoviedb.org/3/tv/popular?api_key=1fb3006bd468938300e6513240f07c00&language=it&page=1`)
        .then(res => {
          store.series = res.data.results
          console.log(res.data.results)
        })
  }

}

</script>

<template>
  <HeaderComp />
  <MainComp />
</template>

<style lang="scss">
@use './style/main.scss'
</style>
