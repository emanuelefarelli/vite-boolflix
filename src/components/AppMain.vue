<template>
    <main>
        <AppSearchbar 
            @searchedMovies="getMovies"
            @searchedTv="getTv"
        />
        <MovieList 
            :movieList = "movieList"
            :tvList = "tvList"
        />
    </main>
</template>

<script>
import AppSearchbar from './AppSeachbar.vue';
import MovieList from './MovieList.vue';
import axios from 'axios';

export default {
    name: 'AppMain',
    data() {
        return {
            apiUrlTv:'https://api.themoviedb.org/3/search/tv',
            apiUrlMovies: 'https://api.themoviedb.org/3/search/movie',
            apiKey: '?api_key=d9eff1916dde6e2b9a1e35533c7273e3',
            // apiQuery: 'Ritorno al futuro',
            movieList:[],
            tvList:[],
        }
    },
    components: {
        AppSearchbar,
        MovieList,
    },
    methods: {
        getTv(needle){
            axios.get(this.apiUrlTv + this.apiKey, {
                params: {
                    query: needle,
                }
            })
                .then( (response) => {
                    // console.log(response);
                    this.tvList = response.data.results;
                    console.log(this.tvList);
                 })
                .catch(function (error) {
                    console.log(error);
                })
        },
        getMovies(needle){
            axios.get(this.apiUrlMovies + this.apiKey, {
                params: {
                    query: needle,
                }
            })
                .then( (response) => {
                    // console.log(response);
                    this.movieList = response.data.results;
                    console.log(this.movieList);
                 })
                .catch(function (error) {
                    console.log(error);
                })
        }
    },
    created(){
        this.getMovies();
        this.getTv();
    },
}
</script>


<style lang="scss" scoped>

</style>