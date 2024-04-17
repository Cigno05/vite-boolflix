<template>

    <div class="navbar bg-body-tertiary">
        <div class="container-lg">
            <a class="navbar-brand">Boolflix</a>
            <form class="d-flex" @submit.prevent="totalSearch()">
                <input class="form-control me-2" type="text" v-model="store.searchText" placeholder="Search">
            </form>
        </div>
    </div>
    <!-- <input type="text" v-model="store.searchText" @keyup.enter="fetchMovieCard()" placeholder="Search" > -->


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

                    store.moviesFound = res.data.results
                    console.log(this.store.moviesFound)


                })
        },

        fetchSerieCard() {

            let query = this.store.searchText
            let API_KEY = 'a27a972eaca218a5475623e4beb58fb7'


            axios
                .get(`https://api.themoviedb.org/3/search/tv`, {
                    params: {
                        api_key: API_KEY,
                        query: query,

                    },
                })
                .then((res) => {
                    console.log(res.data);
                    console.log(res.data.results);

                    store.seriesFound = res.data.results
                    console.log(this.store.seriesFound)


                })
        },

        totalSearch() {
            this.fetchMovieCard()
            this.fetchSerieCard()
            this.store.searchText =''
        }




    },
}
</script>

<style lang="scss" scoped></style>