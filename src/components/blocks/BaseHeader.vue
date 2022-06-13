<template>
  <header class="container">
      <img src="../../assets/img/netflix-logo.png">
      <SearchBar/>
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
    display: flex;
    justify-content: space-between;
    padding: .625rem;
    background-color: black;
    color: lightgray;

    img {
        width: 10%;
    }
    }
   

</style>