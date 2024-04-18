<template>
  <div class="app__content">
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
  data() {
    return {
      store,
    }
  },

}


</script>

<style lang="scss">
@use './style/general';
@use 'bootstrap';



</style>