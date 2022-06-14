<template>
    <section class="container">
        <h1>Films</h1>
        <div class="row">
            <div class="ms_card col-12 col-md-6 col-lg-3" v-for="(film, i) in sharedData.films" :key="i">
                <div class="ms_card">
                    <img v-if="film.poster_path" :src="'https://image.tmdb.org/t/p/w300' + film.poster_path">
                    <img v-esle src="https://via.placeholder.com/306x493">
                    <div class="overlay">
                        <h3>{{film.title}}</h3>
                        <span>{{film.original_title}}</span>
                        <div>
                            <span><lang-flag :iso="film.original_language"/></span>
                            <span v-html="starsVote(film.vote_average)"></span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <h1 class="my-4">TV Series</h1>
        <div class="row">
            <div class="ms_card col-12 col-md-6 col-lg-3" v-for="(serie, index) in sharedData.series" :key="index">
                <img :src="'https://image.tmdb.org/t/p/w342' + serie.poster_path">
                <div class="overlay">
                    <h3>{{serie.name}}</h3>
                    <span>{{serie.original_name}}</span>
                    <div>
                        <span><lang-flag :iso="serie.original_language"/></span>
                        <span v-html="starsVote(serie.vote_average)"></span>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
import sharedData from '@/shared/sharedData'


export default {
    name: 'sectionFilm',
      data() {
        return {
            sharedData,
        }
    },
    methods: {
        starsVote(vote) {
            // creo 2 variabili vuote
            let htmlStars = '';
            let htmlStarsEmpty = '';
            // ciclo per dividere il "voto" diviso 2
            for (let i = 0; i < Math.ceil(vote / 2); i++) {
                htmlStars += '<i class="fa-solid fa-star"></i>';
            }
            // ciclo le stelle vuote su 5 esempio se sopra mi stampa 2 stelle 3 sono vuote
            for (let i = 0; i < 5 - (Math.ceil(vote / 2)); i++) {
                htmlStarsEmpty += '<i class="fa-regular fa-star"></i>';
            }
            // con il dollaro stampa nell html e mi da le stelle piene e vuote
            return `${htmlStars}${htmlStarsEmpty}`;
        }

    },
}

</script>

<style lang="scss" scoped>
.container {
    width: 80%;
    margin: auto;

    img {
        width: 100%;
        height: 100%;
    }

    h1 {
        color: white;
    }

   .overlay {
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        z-index: 1;
        background-color: rgba(0, 0, 0, 0.5);
        color: white;
        opacity: 0;
        transition: opacity 0.3s;
        padding: 10px;
    }   
    .ms_card {
        position: relative;
        margin-bottom: .625rem;
        
        &:hover .overlay {
            opacity: 1;
        }
    }

}



</style>