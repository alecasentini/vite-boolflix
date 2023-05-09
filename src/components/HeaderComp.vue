<script >
import SearchbarComp from './SearchbarComp.vue';
export default {
    name: "HeaderComp",
    components: {
        SearchbarComp,
    }
}
</script>

<template>
    <header class="w-100 d-flex align-items-center">

        <div class="container d-flex align-items-center justify-content-between">
            <img src="../../public/img/logo.png" alt="logo">
            <SearchbarComp />
        </div>



    </header>
</template>

<style lang="scss">
header {
    background-color: black;
    height: 100px;

    h1 {
        color: red;
    }
}
</style>