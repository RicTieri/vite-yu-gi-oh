<template>
  <div class="card m-3 p-0" style="width: 18rem;">
  <img :src="card.card_images[0].image_url" class="card-img-top" :alt="card.name">
  <div class="card-body">
    <h5 class="card-title">{{ card.name }}</h5>
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
  
</style>