<template >
  <div class="wrapper">
    <div class="container fs-4 fw-medium">
      Result : {{ count }}
    </div>
  </div>
</template>
<script>

export default {
  props:{
    count: Number,
  }
}
</script>

<style lang="scss" scoped>
 @use "../style/partial/variables" as*;
  .wrapper{
    background-color: $bg-primary;
    color: white;
    .container{
      background-color: black;
      padding: 1rem;
    }
  }
</style>