<template>
  <AppHeader />
  <AppMain />
</template>

<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import axios from 'axios';
import { store } from './store.js';

export default {
  components: {
    AppHeader,
    AppMain
  },
  data() {
    return {
      store,
      cards:[]
    }
  },
  created() {
    this.getCard();
  },
  methods: {
    getCard() {
      axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
        .then((response) => {
          console.log(response);
          this.store.cards = response.data.data;
        })
        .catch(function (error) {
          console.error(error);
        });
    }
  },
}
</script>

<style lang="scss">
@use './style/general.scss';
</style>