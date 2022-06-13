<template>
    <section class="container justify-content-center py-4">
        <h1>Films</h1>
        
            <div>
               
                <li class="card__poster" v-for="(film, i) in sharedData.films" :key="i">
                    <img :src="'https://image.tmdb.org/t/p/w300' + film.poster_path">
                <div class="hoverlay">
                    <h3>{{film.title}}</h3>
                    <h4>{{film.original_title}}</h4>
                    <h4><lang-flag :iso="film.original_language"/></h4>
                    <h4> <i class="fa-regular fa-star"></i> </h4>
                </div>
                </li>

            <h1>TV Series</h1>
                <li v-for="(series, index) in sharedData.seriess" :key="index">
                    <img :src="'https://image.tmdb.org/t/p/w342' + series.poster_path">
                <div class="hoverlay">
                    <h3>{{series.name}}</h3>
                    <h4>{{series.original_name}}</h4>
                    <h4><lang-flag :iso="series.original_language"/></h4>
                    <h4>{{series.vote_average}}</h4>
                </div>
                </li>
                
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
     starVote(vote) {
                let htmlStars = ''
                for (let i = 0; i < Math.ceil(vote / 2); i++) {
                    htmlStars += '<i class="fa-solid fa-star"></i>';
                }
                return htmlStars;
            }
}

</script>

<style lang="scss" scoped>
.container {
    width: 80%;
    margin: auto;

    h1 {
        color: white;
    }
}
div {
    display: flex;
    flex-wrap: wrap;
    list-style: none;
    justify-content: space-between;
    gap: 30px;
}
img {
    border-radius: 10px;
    width: 200px;
    position: relative;
    
}

.card__poster {
    margin-bottom: 100px;
   
}

.hoverlay {
    position: absolute;
    display: block;
    width: 100%;
}
.hoverlay:hover {
    
}
</style>