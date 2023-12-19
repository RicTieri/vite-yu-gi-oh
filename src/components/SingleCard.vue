<template>
  <div class="card mt-3 mx-3 p-0 text-center" style="width: 18rem;">
  <img :src="card.card_images[0].image_url" class="card-img-top" :alt="card.name">
  <div class="card-body">
    <h4 class="card-title">{{ card.name }}</h4>
    <p>{{ card.archetype }}</p>
  </div>
</div>
</template>

<script>
export default {
  props:{
    card: Object,
  }
}
</script>

<style lang="scss" scoped>
@use '../style/partial/variables' as *;

.card{
  background-color: $bg-primary;
  h4{
    color: white;
  }
}
  
</style>