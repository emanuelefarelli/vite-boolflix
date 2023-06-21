<template>
    <ul>
        <li v-for="movieObj in movieList" :key=movieObj>
            Titolo: {{ movieObj.title }}
            Titolo originale: {{ movieObj.original_title }}
            Lingua originale: {{ movieObj.original_language }}
            Voto: {{ movieObj.vote_average }}
        </li>
    </ul>
</template>

<script>
export default {
    name: 'MovieList',
    data() {
        return {

        }
    },
    props: {
        movieList : Array
    }
}
</script>


<style lang="scss" scoped>
   
</style>