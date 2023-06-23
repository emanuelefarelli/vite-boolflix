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
        <h3 class="movie-title">
            Titolo: {{ movieObj.title }} --
            Titolo originale: {{ movieObj.original_title }}
        </h3>
        <p class="movie-language">
            Lingua originale: <img :src="flagUlr(movieObj.original_language)">
        </p>
        <p class="movie-overview">
            {{ movieObj.overview }}
        </p>
        <div class="movie-vote">
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
    @use '../styles/partials/mixins.scss' as *;
    div.poster{
        @include flex();
        width: 342px;
        height: 506px;
        position: relative;
        div.movie-poster{
            @include flex();
            height: 100%;
            width: 100%;
        }
        h3.movie-title{
            position: absolute;
            padding: 0 1rem;
            top: 2rem;
            color: white;
            display: none;
        }
        p.movie-language{
            position: absolute;
            padding: 0 1rem;
            bottom: 1.5rem;
            color: white;
            display: none;
            img{
                margin-left: 0.6rem;
            }
        }
        div.movie-vote{
            position: absolute;
            padding: 0 1rem;
            bottom: 3.5rem;
            color: white;
            display: none;
        }
        p.movie-overview{
            position: absolute;
            padding: 0 1rem;
            top: 30%;
            color: white;
            height: 260px;
            overflow: auto;
            display: none;
        }
    }
    div.poster:hover{
        div.movie-poster{
            filter: brightness(0.2);
        }
        h3.movie-title{
            display: block;
        }
        p.movie-language{
            display: flex;
            align-items: center;
        }
        div.movie-vote{
            display: block;
        }
        p.movie-overview{
            display: block;
        }
    }
</style>