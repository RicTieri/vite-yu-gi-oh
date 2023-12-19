<template>
  <div class="container-fluid text-center pt-5">
    <select name="search" id="search" class="fs-5 rounded-3 p-1">
      <option v-for="card in cardType" :value="card.archetype_name" @click="$choice(card.archetype_name)">{{ card.archetype_name }}</option>
    </select>
  </div>
</template>

<script>
import axios from 'axios';
export default {

  data() {
    return {
      cardType:[]
    }
  },
  created() {
    this.getType();
  },
  methods:{
    getType() {
      axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php')
        .then((response) => {
          console.log(response);
          this.cardType = response.data;
        })
        .catch(function (error) {
          console.error(error);
        });
    }
  }
}
</script>

<style lang="scss" scoped>
@use '../style/partial/variables' as *;

.container-fluid{
  background-color: $bg-primary;

}
  
</style>