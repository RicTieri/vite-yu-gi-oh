<template>
  <AppHeader />
  <AppFilter />
  <AppMain />
</template>

<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppFilter from './components/AppFilter.vue';
import axios from 'axios';
import { store } from './store.js';

export default {
  components: {
    AppHeader,
    AppFilter,
    AppMain
  },
  data() {
    return {
      store,
    }
  },
  created() {
    this.getCard();
  },
  methods: {
    getCard() {
      axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php',{
        params:{
          num:20,
          offset:0,
          archetype: null
        }
      })
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