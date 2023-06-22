<template>
    <img :src="buildPoster(tvObj.poster_path)" alt="tv series poster">
    <h3>
        Titolo: {{ tvObj.name }} --
        Titolo originale: {{ tvObj.original_name }}
    </h3>
    <p>
        Lingua originale: <img :src="flagUlr(tvObj.original_language)"> {{ tvObj.original_language }}
    </p>
    <p>
        Voto: {{ tvObj.vote_average }}
    </p>
</template>

<script>

    export default {
        data(){
            return{
                flagApiUrl: 'https://www.countryflagicons.com/FLAT/24/',
                posterStartUrl: 'https://image.tmdb.org/t/p/w342'
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
                }
                const langUrl = this.flagApiUrl + lang.toUpperCase() + '.png';
                return langUrl;
            },
            buildPoster(finalUrl){
                const posterUrl = this.posterStartUrl + finalUrl;
                return posterUrl
            }
        },
        props:{
            tvObj : Object,
        },
    }
</script>

<style lang="scss" scoped>

</style>