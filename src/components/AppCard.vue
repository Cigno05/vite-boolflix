<template>
        <li>
            <div class="card mb-4" >
                <!-- <img src="" class="card-img-top" alt="..."> -->
                <div class="card-body">
                    <h5 class="card-title">{{ item.title }}</h5>
                    <p class="card-text">{{ item.overview }}</p>
                </div>
                <ul class="list-group list-group-flush">
                    <li class="list-group-item">Titolo originale: {{ item.original_title }}</li>
                    <li class="list-group-item">Lingua originale: <img :src="lenguafeImgSrc" alt=""><span>{{ lenguageString }}</span></li>
                    <li class="list-group-item">Voto medio: {{ voteAverage }}</li>
                </ul>
            </div>
        </li>
</template>

<script>
import { store } from '../store.js';

export default {
    props: {
        item: {
            type: Object,
            required: true 
        },
    },
    data() {
        return {
            store,

        }
    },
    computed: {
        voteAverage() {
            const vote = Math.floor(this.item.vote_average / 2)
            // console.log(vote)
            const star = 'x'
            const emptyStar = 'o'
            const voteStar = star.repeat(vote) + emptyStar.repeat((5 - vote))
            return voteStar
        },
        lenguafeImgSrc() {
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
        }
    },
}
</script>


<style lang="scss" scoped></style>