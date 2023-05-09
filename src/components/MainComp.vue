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
    background-color: rgb(29, 28, 28);
    height: calc(100vh - 100px);
    overflow-y: scroll;
}
</style>