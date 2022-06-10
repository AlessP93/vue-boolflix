<template>
    <div>
        <form @submit.prevent="searching">
        <input type="text" v-model="text" placeholder="Search Films">
        <button type="submit">Search</button>
        </form>
    </div>
</template>

<script>

import axios from 'axios';
import sharedData from '../../shared/sharedData';

export default {
    name: 'searchBar',
      data() {
        return {
            films: [],
            text: '',
            sharedData: films
        }
    },
    
    methods: {
        searching() {
          console.log(this.text);
            axios.get('https://api.themoviedb.org/3/search/movie', {
            params: {
                api_key: '5c666a321988cb223d7a715dd437c5f7',
                query: this.text,
                language: 'it-IT'
            }
            }).then((response) => {
              this.films = response.data.results;
            }).catch((error) => {
              console.log(error);
            })
        }
    },
}
</script>

<style>

</style>