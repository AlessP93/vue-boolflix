<template>  
    <main>
        <searchFilms/>
    </main>
</template>

<script>
import axios from 'axios';
import searchFilms from '../commons/searchFilms.vue';

export default {
    name: 'BaseMain',
    data() {
        return {
            films: [],
        }
    },
    components: {
    searchFilms,
    },
    // methods: {
    //     filmFound:
    // },
    
   created() {
    axios.get('https://api.themoviedb.org/3/search/movie', {
    params: {
        api_key: '5c666a321988cb223d7a715dd437c5f7',
        query: 'original_title',
        language: 'it-IT'
    }
    }).then((response) => {
      this.films = response.data.results;
    }).catch((error) => {
      console.log(error);
    })
  },
}

</script>

<style lang="scss" scoped>

</style>