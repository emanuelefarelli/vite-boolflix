<template>
    <section class="input-search">
        <input type="text" v-model="inputSearch">
        <button>
            Search
        </button>
    </section>
</template>

<script>
export default {
    name: 'AppSearchbar',
    data() {
        return {

        }
    },
}
</script>


<style lang="scss" scoped>
    @use '../styles/partials/mixins.scss' as *;
    section.input-search{
        @include flex();
        padding: 2rem;
        input,
        button{
            padding: 0.3rem;
            margin-right: 1rem;
        }
    }
</style>