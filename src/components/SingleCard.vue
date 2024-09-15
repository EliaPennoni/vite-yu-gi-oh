<script>
export default {
  props: {
    card: Object,
  },
};
</script>

<template>
  <div class="card">
    <img :src="card.card_images[0].image_url" alt="Card Image" />
    <div class="info">
      <div>{{ card.name }}</div>
      <div>{{ card.archetype }}</div>
    </div>
  </div>
</template>

<style lang='scss' scoped>
@import "bootstrap/scss/bootstrap";
</style>
