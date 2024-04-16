<template>
  <div>
    <h1>App</h1>
    <AppHeader />
    <AppContents />
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue';
import AppContents from './components/AppContents.vue';
import { store } from './store.js';
import axios from 'axios';

export default {
  components: {
    AppHeader,
    AppContents,
  },
  methods: {
    fetchMovieCard() {
      let query = 'ritorno al futuro'
			let API_KEY = 'e99307154c6dfb0b4750f6603256716d'

      axios
				.get(`https://api.themoviedb.org/3/search/movie`, {
					params: {
						api_key: API_KEY,
						query: query,
						
					},
				})
				.then((res) => {
					console.log(res.data)
					console.log(res.data.results)
				})
    },
  },
  created () {
    this.fetchMovieCard();
  },
}


</script>

<style lang="scss">
@use './style/general';

</style>