<template>  
    <main class="container-fluid">
        <sectionFilm/>
    </main>
</template>

<script>
import sectionFilm from '../sections/sectionFilm.vue'

export default {
    name: 'BaseMain',
    components: {
      sectionFilm
    },
}

</script>

<style lang="scss" scoped>
main {
 background-color: #303030;
 min-height: 100vh;
}
</style>