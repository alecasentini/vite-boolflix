<script >
import SearchResultComp from './SearchResultComp.vue';

export default {
    name: "MainComp",
    components: {
        SearchResultComp,
    },

}
</script>

<template>
    <main class="w-100 d-flex justify-content-center align-items-center">
        <SearchResultComp />
    </main>
</template>

<style lang="scss">
main {
    background-color: rgb(28, 28, 28);
    height: calc(100vh - 70px);
    overflow-y: scroll;
}
</style>