<template>
  <div>
    <h2>
        {{ movieTitle }}
    </h2>
    <i class="fa-solid fa-film"></i>
  </div>
</template>

<script>
export default {
    data(){
        return{
            
        }
    },
    props:{
        movieTitle : String
    }
}
</script>

<style lang="scss" scoped>
    @use '../styles/partials/variables.scss' as *;
    @use '../styles/partials/mixins.scss' as *;

    div{
        @include flex(column);
        width: 342px;
        height: 506px;
        background-color: rgb(143, 143, 143);
        padding: 1rem;
        h2,
        i{
            color: rgb(37, 37, 37);
        }
        h2{
            font-size: $fontSizeL;
            text-align: center;
            margin-bottom: 2.5rem;
        }
        i{
            font-size: $fontSizeXL;
        }
    }
</style>