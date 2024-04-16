<template>
    <div>
        <li v-for="movie in store.moviesFound">
            <p>{{ movie.original_title }}</p>
        </li>
    </div>
</template>

<script>
import { store } from '../store.js';

    export default {
        data() {
            return {
                store,
            }
        },
    }
</script>

<style lang="scss" scoped>

</style>