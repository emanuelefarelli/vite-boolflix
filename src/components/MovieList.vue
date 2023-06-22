<template>
    <ul>
        <li v-for="movieObj in movieList" :key=movieObj>
            <SingleMovie :movieObj = "movieObj"/>
        </li>
    </ul>
</template>

<script>
import SingleMovie from './SingleMovie.vue';

export default {
    name: 'MovieList',
    data() {
        return {

        }
    },
    props: {
        movieList : Array
    },
    components: {
        SingleMovie,
    }
}
</script>


<style lang="scss" scoped>
   
</style>