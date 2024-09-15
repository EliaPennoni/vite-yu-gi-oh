<script>
import axios from "axios";
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";

export default {
  data() {
    return {
      allMagicCards: [],
      archetypes: [], 
      selectedArchetype: "",   
    };
  },
  created() {
    axios
      .get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0")
      .then((res) => {
        this.allMagicCards = res.data.data;

        const archetypeSet = new Set();
        this.allMagicCards.forEach((card) => {
          if (card.archetype) {
            archetypeSet.add(card.archetype);
          }
        });
        this.archetypes = Array.from(archetypeSet);
      })
      .catch((error) => console.error("Errore nell'API call", error));
  },
  computed: {
    filteredMagicCards() {
      if (!this.selectedArchetype) {
        return this.allMagicCards;
      }
      return this.allMagicCards.filter(
        (card) => card.archetype === this.selectedArchetype
      );
    },
  },
  components: {
    AppHeader,
    AppMain,
  },
};
</script>

<template>
  <div>
    <AppHeader :MagicCardsNumber="filteredMagicCards.length" />

    <div class="select">
      <select v-model="selectedArchetype" class="form-select" aria-label="Filter by archetype">
        <option value="">All Archetypes</option>
        <option v-for="(archetype, index) in archetypes" :key="index" :value="archetype">
          {{ archetype }}
        </option>
      </select>
    </div>

    <AppMain :MagicCards="filteredMagicCards" />
  </div>
</template>

<style lang='scss' scoped>
@import "bootstrap/scss/bootstrap";

.select {
  margin: 10px 0;
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
