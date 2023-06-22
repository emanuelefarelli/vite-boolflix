<template>
    <section class="list">
        <ul class="movie-list">
            <li>
                <h1>
                    FILM:
                </h1>
            </li>
            <li v-for="movieObj in movieList" :key=movieObj>
                <SingleMovie :movieObj = "movieObj"/>
            </li>
        </ul>
        <ul class="tv-list">
            <li>
                <h1>
                    SERIE TV:
                </h1>
            </li>
            <li v-for="tvObj in tvList" :key=tvObj>
                <SingleTv :tvObj = "tvObj"/>
            </li>
        </ul>
    </section>
</template>

<script>
import SingleMovie from './SingleMovie.vue';
import SingleTv from './SingleTv.vue';

export default {
    name: 'MovieList',
    data() {
        return {

        }
    },
    props: {
        movieList : Array,
        tvList : Array
    },
    components: {
        SingleMovie,
        SingleTv
    }
}
</script>


<style lang="scss" scoped>
    @use '../styles/partials/mixins.scss' as *;
    section.list{
        @include flex(row,space-between,flex-start,wrap);
        width: 80%;
        margin: 0 auto;
        ul{
            width: 45%
        }
    }
</style>