<template>
  <div class="container-fluid text-center py-3">
    <select name="search" id="search" class="fs-5 rounded-3 p-1" v-model="selectedValue" @change="$emit('choice', selectedValue)">
      <option :value="null">All</option>
      <option v-for="card in cardType" :value="card.archetype_name">{{ card.archetype_name }}</option>
    </select>
  </div>
</template>

<script>
import axios from 'axios';


export default {

  data() {
    return {
      cardType:[],
      selectedValue: null
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