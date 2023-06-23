<template>
    <div v-if="tvObj.poster_path === null" class= "tv-poster">
        <MissingPoster 
            :movieTitle = "tvTitle"
        />
    </div>
    <div v-else class="tv-poster">
        <img :src="buildPoster(tvObj.poster_path)" alt="movie poster">
    </div>
    <h3>
        Titolo: {{ tvObj.name }} --
        Titolo originale: {{ tvObj.original_name }}
    </h3>
    <p>
        Lingua originale: <img :src="flagUlr(tvObj.original_language)">
    </p>
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

</style>