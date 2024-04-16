<template>
    <div>
        <h1>Header</h1>
        <input type="text" v-model="store.searchText" @keyup.enter="fetchMovieCard()">

    </div>
</template>

<script>
import { store } from '../store.js';
import axios from 'axios';

export default {
    data() {
        return {
            store: store,


        }
    },
    methods: {
        fetchMovieCard() {
            let query = this.store.searchText
            let API_KEY = 'a27a972eaca218a5475623e4beb58fb7'

            axios
                .get(`https://api.themoviedb.org/3/search/movie`, {
                    params: {
                        api_key: API_KEY,
                        query: query,

                    },
                })
                .then((res) => {
                    console.log(res.data);
                    console.log(res.data.results);

                    for (let index = 0; index < res.data.results.length; index++) {
                        let movie = res.data.results[index]
                        this.store.moviesFound.push(movie)
                    }
                    console.log(this.store.moviesFound)


                })
        },

    },
}
</script>

<style lang="scss" scoped></style>