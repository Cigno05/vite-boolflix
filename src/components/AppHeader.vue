<template>

    <nav class="navbar ">
        <div class="container-lg">
            <h1 class="navbar-brand">Boolflix</h1>
            <form class="d-flex" @submit.prevent="totalSearch()">
                <input class="form-control me-2" type="text" v-model="store.searchText" placeholder="Search">
            </form>
        </div>
    </nav>
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
                    this.store.moviesFound = [];

                    for (let index = 0; index < res.data.results.length; index++) {
                        let movie = res.data.results[index]
                        this.store.moviesFound.push(movie)
                    }
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
                    this.store.seriesFound = [];

                    for (let index = 0; index < res.data.results.length; index++) {
                        let serie = res.data.results[index]
                        this.store.seriesFound.push(serie)
                    }
                    console.log(this.store.seriesFound)
                })
        },

        totalSearch() {
            this.fetchMovieCard()
            this.fetchSerieCard()
            this.store.searchText = ''
        }




    },
}
</script>

<style lang="scss" scoped>
.navbar {
    background-color: #050505;
    
    .navbar-brand {
        color: red;
        font-size: 48px;
    }

}
</style>