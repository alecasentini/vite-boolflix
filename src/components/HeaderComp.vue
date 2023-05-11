<script >
import SearchbarComp from './SearchbarComp.vue';
import SelectGenereComp from './SelectGenereComp.vue';
export default {
    name: "HeaderComp",
    components: {
        SearchbarComp,
        SelectGenereComp
    },
    methods: {
        refreshPage() {
            location.reload();
        }
    }
}
</script>

<template>
    <header class="w-100 d-flex align-items-center">

        <div class="container d-flex align-items-center justify-content-between">
            <a href="#" @click="refreshPage"><img src="../../public/img/logo.png" alt="logo" /></a>
            <SearchbarComp />
            <SelectGenereComp />
        </div>



    </header>
</template>

<style lang="scss">
header {
    background-color: black;
    height: 70px;

    img {
        height: 70px;
    }
}
</style>