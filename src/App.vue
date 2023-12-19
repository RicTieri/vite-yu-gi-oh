<template>
  <AppHeader />
  <AppFilter @choice="getCard"/>
  <AppCounter 
  :count="this.store.cards.length"/>
  <AppMain />
</template>

<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppFilter from './components/AppFilter.vue';
import AppCounter from './components/AppCounter.vue';
import axios from 'axios';
import { store } from './store.js';

export default {
  components: {
    AppHeader,
    AppFilter,
    AppCounter,
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
    getCard(cardType) {
      axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php',{
        params:{
          num:20,
          offset:0,
          archetype: cardType
        }
      })
        .then((response) => {
          console.log(response);
          this.store.cards = response.data.data;
        })
        .catch(function (error) {
          console.error(error);
        });
    },
  },
}
</script>

<style lang="scss">
@use './style/general.scss';
</style>