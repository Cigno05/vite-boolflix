<template>
    <div>
        <h2>Movies</h2>
        <ul class="d-flex gap-4 flex-wrap" v-if="store.moviesFound.length !== 0">
            <AppCard v-for="movie in store.moviesFound" :key="movie.id" :item="movie" />
        </ul>
        <h2>Serie</h2>
        <ul class="d-flex gap-4 flex-wrap" v-if="store.seriesFound.length !== 0">
            <AppCard v-for="serie in store.seriesFound" :key="serie.id" :item="serie" />
        </ul>

    </div>
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

<style lang="scss" scoped></style>