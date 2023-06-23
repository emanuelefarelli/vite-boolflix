<template>
    <div class="poster">
        <div v-if="movieObj.poster_path === null" class= "movie-poster">
            <MissingPoster 
                :movieTitle = "movieTitle"
            />
        </div>
        <div v-else class="movie-poster">
            <img :src="buildPoster(movieObj.poster_path)" alt="movie poster">
        </div>
        <h3>
            Titolo: {{ movieObj.title }} --
            Titolo originale: {{ movieObj.original_title }}
        </h3>
        <p>
            Lingua originale: <img :src="flagUlr(movieObj.original_language)"> {{ movieObj.original_language }}
        </p>
        <div v-if="castVote(movieObj.vote_average) === 0">
            <i class="fa-regular fa-star"></i>
            <i class="fa-regular fa-star"></i>
            <i class="fa-regular fa-star"></i>
            <i class="fa-regular fa-star"></i>
            <i class="fa-regular fa-star"></i>
        </div>
        <div v-if="castVote(movieObj.vote_average) === 1">
            <i class="fa-solid fa-star"></i>
            <i class="fa-regular fa-star"></i>
            <i class="fa-regular fa-star"></i>
            <i class="fa-regular fa-star"></i>
            <i class="fa-regular fa-star"></i>
        </div>
        <div v-if="castVote(movieObj.vote_average) === 2">
            <i class="fa-solid fa-star"></i>
            <i class="fa-solid fa-star"></i>
            <i class="fa-regular fa-star"></i>
            <i class="fa-regular fa-star"></i>
            <i class="fa-regular fa-star"></i>
        </div>
        <div v-if="castVote(movieObj.vote_average) === 3">
            <i class="fa-solid fa-star"></i>
            <i class="fa-solid fa-star"></i>
            <i class="fa-solid fa-star"></i>
            <i class="fa-regular fa-star"></i>
            <i class="fa-regular fa-star"></i>
        </div>
        <div v-if="castVote(movieObj.vote_average) === 4">
            <i class="fa-solid fa-star"></i>
            <i class="fa-solid fa-star"></i>
            <i class="fa-solid fa-star"></i>
            <i class="fa-solid fa-star"></i>
            <i class="fa-regular fa-star"></i>
        </div>
        <div v-if="castVote(movieObj.vote_average) === 5">
            <i class="fa-solid fa-star"></i>
            <i class="fa-solid fa-star"></i>
            <i class="fa-solid fa-star"></i>
            <i class="fa-solid fa-star"></i>
            <i class="fa-solid fa-star"></i>
        </div>
    </div>
</template>

<script>
    import MissingPoster from './missingPoster.vue';

    export default {
        data(){
            return{
                flagApiUrl: 'https://www.countryflagicons.com/FLAT/24/',
                posterStartUrl: 'https://image.tmdb.org/t/p/w342',
                movieTitle: this.movieObj.title
            }
        },
        methods: {
            flagUlr(lang){
                if (lang === 'en'){
                    lang = 'gb';
                }else if(lang === 'zh'){
                    lang = 'cn';
                }else if(lang === 'ja'){
                    lang = 'jp';
                }else if(lang === 'hi'){
                    lang = 'in';
                }else if(lang === 'ko'){
                    lang = 'kr';
                }else if(lang === 'cs'){
                    lang = 'sx';
                }
                const langUrl = this.flagApiUrl + lang.toUpperCase() + '.png';
                return langUrl;
            },
            buildPoster(finalUrl){
                const posterUrl = this.posterStartUrl + finalUrl;
                console.log("MOVIE POSTER: ");
                return posterUrl
            },
            castVote(vote){
                const castedVote = Math.ceil((vote * 5) / 10);
                return castedVote
            }
        },
        components: {
            MissingPoster
        },
        props:{
            movieObj : Object,
        },
    }
</script>

<style lang="scss" scoped>

</style>