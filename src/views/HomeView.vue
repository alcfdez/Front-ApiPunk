<script setup>
import { onBeforeMount, ref, computed } from "vue";
import BeerService from "../services/BeerService";
import Header from "../components/Header.vue";
import BeersCard from "../components/BeersCard.vue";

const beerService = new BeerService();
const beers = ref([]);

onBeforeMount(async () => {
  await beerService.fetchAllBeers();
  beers.value = beerService.getBeers();
  console.log(beers.value);
});

let input = ref("");

function filteredBeers() {
  if (!input.value) return beers.value;
  return beers.value.filter((beer) =>
    beer.name.toLowerCase().includes(input.value.toLowerCase())
  );
}
</script>

<template>
  <Header />
  <main>
    <section class="search">
      <div class="search-input">
        <input
          type="text"
          v-model="input"
          placeholder="search beer by name..."
        />
      </div>

      <div class="search-error" v-if="input && !filteredBeers().length">
        <p>No results found!</p>
      </div>
    </section>

    <section class="cards-view">
      <BeersCard v-for="beer in filteredBeers()" :beer="beer" />
    </section>
  </main>
</template>

<style lang="scss" scoped>
@import "../scss/styles.scss";

main {
  background-color: $light-beige;
  margin: 0;
  display: flex;
  flex-direction: column;
  align-items: center;

  .search {
    width: 60%;

    &-input {
      margin-top: 2em;
      display: flex;
      flex-direction: row;
      align-items: center;
      border-radius: 5px;
      height: 2em;
      background-color: $light-brown;
      font-size: 1em;
      font-family: $font-text-2;

      input {
        margin-left: 0.5em;
        outline: none;
      }
    }

    &-error {
      margin-top: 20%;
      font-family: $font-text-2;
      font-weight: 600;
      font-size: 5em;
    }
  }
  .cards-view {
    margin-top: 2em;
    display: flex;
    flex-wrap: wrap;
    gap: 1.5em;
    justify-content: center;
    align-items: center;
  }
}
</style>
