<template>
  <main class="py-5">
    <div class="container">
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
@use '../style/partial/variables' as *;

main{
  background-color: $bg-primary;

  .container{
    background-color: white;
  }
}

</style>