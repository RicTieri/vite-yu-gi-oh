<template>
  <main class="">
    <div class="container p-0">
      <AppFilter @choice="getCard"/>
  <AppCounter 
  :count="this.store.cards.length"/>
      <div class="row justify-content-center">
        <SingleCard v-for="card in store.cards"
        :card="card"      
        />
      </div>
    </div>
  </main>
</template>

<script>
import SingleCard from './SingleCard.vue';
import AppFilter from './AppFilter.vue';
import AppCounter from './AppCounter.vue';
import axios from 'axios';
import { store } from '../store.js';

export default {
  components:{
    AppFilter,
    AppCounter,
    SingleCard,
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

<style lang="scss" scoped>
@use '../style/partial/variables' as *;

main{
  background-color: $bg-primary;

  .container{
    background-color: white;
  }
}

</style>