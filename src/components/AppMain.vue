<template>
    <main>
        <AppSearchbar/>
    </main>
</template>

<script>
import AppSearchbar from './AppSeachbar.vue';
import axios from 'axios';

export default {
    name: 'AppMain',
    data() {
        return {
            apiUrl: 'https://api.themoviedb.org/3/search/movie',
            apiKey: '?api_key=d9eff1916dde6e2b9a1e35533c7273e3',
            apiQuery: 'Ritorno al futuro',
            movieList:[],
        }
    },
    components: {
        AppSearchbar
    },
    methods: {
        getMovies(needle){
            axios.get(this.apiUrl + this.apiKey, {
                params: {
                    query: this.apiQuery,
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
    }
}
</script>


<style lang="scss" scoped>

</style>