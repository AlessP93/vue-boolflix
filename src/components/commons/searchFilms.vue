<template>
    <div>
        <input type="text" placeholder="Search Film" @filmFound="$emit('pippo', discovered )">
        <button>search</button>
    </div>
</template>

<script>
export default {
    name: 'searchFilms',
}
</script>

<style lang="scss" scoped>

</style>