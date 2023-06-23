<template>
    <section class="list" v-if="(movieList.length === 0) && (tvList.length === 0)">
        <h1>
            FILM
        </h1>
        <ul class="movie-list">
            <h2>
                Cerca un film!
            </h2>
        </ul>
        <h1>
            SERIE TV
        </h1>
        <ul class="tv-list">
            <h2>
                Cerca una serie tv!
            </h2>
        </ul>
    </section>
    
    <section class="list" v-else>
        <h1>
            FILM
        </h1>
        <ul class="movie-list">
            <li v-for="movieObj in movieList" :key=movieObj>
                <SingleMovie :movieObj = "movieObj"/>
            </li>
        </ul>
        <h1>
            SERIE TV
        </h1>
        <ul class="tv-list">
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
    @use '../styles/partials/variables.scss' as *;
    section.list{
        @include flex(column,space-between,flex-start,wrap);
        width: 80%;
        margin: 0 auto;
        overflow: hidden;
        h1{
            width: 100%;
            padding: 1.5rem;
            font-size: $fontSizeL;
            text-align: center;
            color: white;
            background-color: rgb(29, 29, 29);
        }
        ul{
            @include flex(row,flex-start,center,nowrap);
            overflow: auto;
            width: 100%;
            height: 600px;
            padding: 2rem;
            margin-bottom: 1.5rem;
            background-color: rgb(48, 48, 48);
            li{
                margin-right: 2.5rem;
            }
            h2{
                width: 100%;
                font-size: $fontSizeL;
                color: white;
                text-align: center;
            }
        }
    }
</style>