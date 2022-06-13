<template>
    <header>
        <div class="container-fluid">
            <img src="../../assets/img/netflix-logo.png">
            <SearchBar/>
        </div>
    </header>
</template>

<script>
import SearchBar from '../commons/searchBar.vue';
export default {
    components: { SearchBar }
}
</script>

<style lang="scss" scoped>
header {
    padding: .625rem;
    background-color: black;
    color: lightgray;

    .container-fluid {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    img {
        width: 10%;
    }

    }
   

</style>