<script>
export default {
  props: {
    MagicCardsNumber: Number,
  },
};
</script>

<template>
  <header>
    <div class="logo">
      <img src="" alt="" />
    </div>
    <div class="titolo">
      <h2>Yu-Gi-Oh API</h2>
    </div>
    <div class="row mb-3">
      <div class="col-12">
        <h5>Numero carte trovate: {{ MagicCardsNumber }}</h5>
      </div>
    </div>
  </header>
</template>

<style lang='scss' scoped>
@import "bootstrap/scss/bootstrap";
</style>
