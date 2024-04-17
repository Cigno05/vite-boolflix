<template>
    <div>
        <h1>Contents</h1>
        <ul><!--  aggiungere il v-if -->
            <AppCard v-for="movie in store.moviesFound" :key="movie.id" :item="movie" />
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