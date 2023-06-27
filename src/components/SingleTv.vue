<template>
    <div class="poster">
        <div v-if="tvObj.poster_path === null" class= "tv-poster">
            <MissingPoster 
                :movieTitle = "tvTitle"
            />
        </div>
        <div v-else class="tv-poster">
            <img :src="buildPoster(tvObj.poster_path)" alt="movie poster">
        </div>
        <h3 class="tv-title">
            Titolo: {{ tvObj.name }} --
            Titolo originale: {{ tvObj.original_name }}
        </h3>
        <p class="tv-language">
            Lingua originale: <img :src="flagUlr(tvObj.original_language)">
        </p>
        <p class="tv-overview">
            {{ tvObj.overview }}
        </p>
        <div class="tv-vote">
            <div v-if="castVote(tvObj.vote_average) === 0">
                <i class="fa-regular fa-star"></i>
                <i class="fa-regular fa-star"></i>
                <i class="fa-regular fa-star"></i>
                <i class="fa-regular fa-star"></i>
                <i class="fa-regular fa-star"></i>
            </div>
            <div v-if="castVote(tvObj.vote_average) === 1">
                <i class="fa-solid fa-star"></i>
                <i class="fa-regular fa-star"></i>
                <i class="fa-regular fa-star"></i>
                <i class="fa-regular fa-star"></i>
                <i class="fa-regular fa-star"></i>
            </div>
            <div v-if="castVote(tvObj.vote_average) === 2">
                <i class="fa-solid fa-star"></i>
                <i class="fa-solid fa-star"></i>
                <i class="fa-regular fa-star"></i>
                <i class="fa-regular fa-star"></i>
                <i class="fa-regular fa-star"></i>
            </div>
            <div v-if="castVote(tvObj.vote_average) === 3">
                <i class="fa-solid fa-star"></i>
                <i class="fa-solid fa-star"></i>
                <i class="fa-solid fa-star"></i>
                <i class="fa-regular fa-star"></i>
                <i class="fa-regular fa-star"></i>
            </div>
            <div v-if="castVote(tvObj.vote_average) === 4">
                <i class="fa-solid fa-star"></i>
                <i class="fa-solid fa-star"></i>
                <i class="fa-solid fa-star"></i>
                <i class="fa-solid fa-star"></i>
                <i class="fa-regular fa-star"></i>
            </div>
            <div v-if="castVote(tvObj.vote_average) === 5">
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
                tvTitle: this.tvObj.name
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
                }else if(lang === 'ta'){
                    lang = 'in';
                }
                const langUrl = this.flagApiUrl + lang.toUpperCase() + '.png';
                return langUrl;
            },
            buildPoster(finalUrl){
                const posterUrl = this.posterStartUrl + finalUrl;
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
            tvObj : Object,
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
        div.tv-poster{
            @include flex();
            height: 100%;
            width: 100%;
        }
        h3.tv-title{
            position: absolute;
            padding: 0 1rem;
            top: 2rem;
            color: white;
            display: none;
        }
        p.tv-language{
            position: absolute;
            padding: 0 1rem;
            bottom: 1.5rem;
            color: white;
            display: none;
            img{
                margin-left: 0.6rem;
            }
        }
        div.tv-vote{
            position: absolute;
            padding: 0 1rem;
            bottom: 3.5rem;
            color: white;
            display: none;
        }
        p.tv-overview{
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
        div.tv-poster{
            filter: brightness(0.2);
        }
        h3.tv-title{
            display: block;
        }
        p.tv-language{
            display: flex;
            align-items: center;
        }
        div.tv-vote{
            display: block;
        }
        p.tv-overview{
            display: block;
        }
    }
</style>