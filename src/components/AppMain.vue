<script>
import SingleCard from './SingleCard.vue';

export default {
  props: {
    MagicCards: Array,
  },
  components: {
    SingleCard,
  },
};
</script>

<template>
  <main>
    <div class="background">
      <div class="row cards-container">
        <div
          v-for="(card, index) in MagicCards"
          :key="index"
          class="col-3 card"
        >
          <!-- Usa solo il componente SingleCard per mostrare le card -->
          <SingleCard :card="card" />
        </div>
      </div>
    </div>
  </main>
</template>

<style lang='scss' scoped>
@import "bootstrap/scss/bootstrap";

.background {
  background-color: orange;
}

.cards-container {
  width: 1000px;
  margin: 0 auto;
  background-color: white;
  padding: 30px;
}

.info {
  background-color: orange;
  margin-bottom: 30px;
}

.card img {
  width: 100%;
}
</style>
