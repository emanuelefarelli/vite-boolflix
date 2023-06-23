<template>
    <header>
        <img src="https://www.smartworld.it/wp-content/uploads/mobile/2016/06/netflix-nuova-icona-800x534.png" alt="Immagine del logo non di netflix">
        <h1>
            BoolFlix!
        </h1>
    </header>  
</template>

<script>
export default {
    name: 'AppHeader',
    data() {
        return {

        }
    },
}
</script>


<style lang="scss" scoped>
    @use '../styles/partials/mixins.scss' as *; 
    header{
        height: 150px;
        background-color: rgb(20, 20, 20);
        @include flex(row,space-around, center);
        img{
            height: 100%;
        }
        h1{
            font-size: 4rem;
            color: white;
        }
    }
</style>