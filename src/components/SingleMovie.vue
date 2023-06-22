<template>
    <h3>
        Titolo: {{ movieObj.title }} --
        Titolo originale: {{ movieObj.original_title }}
    </h3>
    <p>
        Lingua originale: <img :src="flagUlr(movieObj.original_language)">
    </p>
    <p>
        Voto: {{ movieObj.vote_average }}
    </p>
</template>

<script>

    export default {
        data(){
            return{
                flagApiUrl: 'https://www.countryflagicons.com/FLAT/24/',
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
                }
                const langUrl = this.flagApiUrl + lang.toUpperCase() + '.png';
                return langUrl;
            }
        },
        props:{
            movieObj : Object,
        },
    }
</script>

<style lang="scss" scoped>

</style>