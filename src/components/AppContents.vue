<template>
    <main>
        <div class="container-fluid">
            <div class="row">

                <h2 v-if="store.moviesFound.length !== 0">Movies</h2>
                <ul class="d-flex gap-2 overflow-x-auto" v-if="store.moviesFound.length !== 0">
                    <AppCard v-for="movie in store.moviesFound" :key="movie.id" :item="movie" />
                </ul>
                <h2 v-if="store.seriesFound.length !== 0">Serie TV</h2>
                <ul class="d-flex gap-2 overflow-x-auto" v-if="store.seriesFound.length !== 0">
                    <AppCard v-for="serie in store.seriesFound" :key="serie.id" :item="serie" />
                </ul>
            </div>
        </div>
    </main>
</template>




<script>
import AppCard from './AppCard.vue'
import { store } from '../store.js'
export default {
    components: {
        AppCard,
    },
    data() {
        return {
            store: store,
        }
    },
}
</script>

<style lang="scss" scoped>
    .container-fluid {
        background-color: #050505;
        color: red;
    }
</style>