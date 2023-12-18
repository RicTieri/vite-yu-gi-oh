<template>
  <main class="container">
    <div class="row">
      <SingleCard v-for="card in store.cards"
      :card="card"      
      />
    </div>
  </main>
</template>

<script>
import SingleCard from './SingleCard.vue';
import { store } from '../store.js';

export default {
  components:{
    SingleCard,
  },
  data() {
    return {
      store,
    }
  },
}
</script>

<style lang="scss" scoped>

</style>