<template>
    <div class="input__text">
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
            text: '',
            sharedData,
        }
    },
    // METODO CHE PRENDE L AZIOS DI TUTTI I FILM
    methods: {
        searching() { // SEARCHING E LA L EVENTO NELL ABARRA DI RICERCA
          console.log(this.text);
            axios.get('https://api.themoviedb.org/3/search/movie', {
            params: {
                api_key: '5c666a321988cb223d7a715dd437c5f7',
                query: this.text,
                language: 'it-IT'
            }
            }).then((response) => {
              this.sharedData.films = response.data.results;
            }).catch((error) => {
              console.log(error);
            })
        // METODO CHE PRENDE L AZIOS DI TUTTE LE SERIE TV
            axios.get('https://api.themoviedb.org/3/search/tv', {
            params: {
                api_key: '5c666a321988cb223d7a715dd437c5f7',
                query: this.text,
                language: 'it-IT'
            }
            }).then((response) => {
              this.sharedData.series = response.data.results;
            }).catch((error) => {
              console.log(error);
            })
        },
    },
}
</script>

<style lang="scss" scoped>
.input__text {
        align-self: center;

        input, button {
            height: 30px;
            background-color: li;
      }
    }
</style>