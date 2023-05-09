<script >
import HeaderComp from './components/HeaderComp.vue'
import MainComp from './components/MainComp.vue';

export default {
  name: "App",
  components: {
    HeaderComp,
    MainComp
  },

}

</script>

<template>
  <HeaderComp />
  <MainComp />
</template>

<style lang="scss">
@use './style/main.scss'
</style>
