<template>

    <li>
        <div class="card-image mb-4">

            <img :src="posterImgSrc" class="card-img-top" alt="...">

            <div class="card-image overlay">

                <div class="card-body">
                    <ul class="list-group list-group-flush">
                        <li class="item">
                            <h3>{{ item.title ?? item.name }}</h3>
                        </li>
                        <li class="item" v-if="item.overview !== ''">
                            <h5>Descrizione:</h5>
                            <p>{{ item.overview }}</p>
                        </li>
                        <li class="item">Titolo originale: {{ item.original_title ?? item.original_name }}
                        </li>
                        <li class="item">Lingua originale: <img :src="lenguageImgSrc" alt=""><span>{{ lenguageString }}</span></li>
                        <ul class="d-flex p-0 justify-content-center gap-2">
                            <li v-for="star in Math.floor(item.vote_average / 2)" :key="star"><font-awesome-icon :icon="['fas', 'star']" /></li>
                            <li v-for="star in (5 - Math.floor(item.vote_average / 2))" :key="star"><font-awesome-icon :icon="['far', 'star']" /></li>
                            
                        </ul>

                    </ul>
                </div>
            </div>
        </div>
    </li>
</template>

<script>
import { store } from '../store.js';

export default {
    props: {
        item: {
            type: Object,
            required: true,
            
        },
    },
    data() {
        return {
            store,

        }
    },
    computed: {
        lenguageImgSrc() {
            let src

            if (this.item.original_language === 'en' || this.item.original_language === 'it' || this.item.original_language === 'es' || this.item.original_language === 'ja') {
                src = `/img/${this.item.original_language}.png`
                // console.log('flag')
            }

            return src
        },
        lenguageString() {
            let string

            if (this.item.original_language === 'en' || this.item.original_language === 'it' || this.item.original_language === 'es' || this.item.original_language === 'ja') {
                string = '';
            } else {
                string = this.item.original_language
            }

            return string
        },
        posterImgSrc() {
            let poster = `https://image.tmdb.org/t/p/w342${this.item.poster_path}`;
            if (this.item.poster_path === null) {
                poster = `/img/imgNotFound.png`;
            }

            // `https://image.tmdb.org/t/p/w342${this.item.poster_path}`
            return poster
        },


    },
}
</script>

<style lang="scss" scoped>
.card-image {
    width: 250px;
    height: 400px;
    background-color: black;
    color: white;
    position: relative;
    border-radius: 5px;

    &>img {
        height: 100%;
        object-fit: cover;
        border-radius: 5px;
    }

    li {
        background-color: #232323;
        color: white;
    }
}


.card-image.overlay {
    position: absolute;
    opacity: 0;
    overflow-y: auto;
    top: 0;

    background-color: #232323;

    &:hover {
        opacity: 0.85;
    }
}

.item {
    img {
        width: 25px;
    }
}
</style>