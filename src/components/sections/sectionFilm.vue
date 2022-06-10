<template>
    <section>
        <h2>Films</h2>
        <ul>
        <li v-for="(film, i) in films" :key="i">
            <img src="https://image.tmdb.org/t/p/w342/:film.homepage" :alt="film.title">
            <h3>{{film.title}}</h3>
            <h4>{{film.original_title}}</h4>
            <h4><lang-flag :iso="film.original_language"/></h4>
            <h4>{{film.vote_average}}</h4>
        </li>
        </ul>
    </section>
</template>

<script>


export default {
    name: 'sectionFilm',
    
}
</script>

<style lang="scss" scoped>
section {
    background-color: red;
    height: 100px;
}
</style>