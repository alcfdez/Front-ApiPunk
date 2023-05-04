<script setup>
import { onBeforeMount, ref , computed} from 'vue';
import BeerService from '../services/BeerService'
import Header from '../components/Header.vue';
import BeersCard from '../components/BeersCard.vue';

const beerService = new BeerService();
const beers = ref ([]);

onBeforeMount(async() => {
  await beerService.fetchAllBeers();
  beers.value = beerService.getBeers();
  console.log(beers.value);
});


let input = ref ("");

function filteredBeers() {
  if (!input.value) return beers.value 
  return beers.value.filter(
    (beer) => 
  beer.name.toLowerCase().includes(input.value.toLowerCase())
  );
}

</script>

<template>

<Header/>
<main>
<section class="search">
  <div class="input-search">
      <i class="fa-solid fa-magnifying-glass" style="color: #adadad"></i>
      <input
        type="text"
        v-model="input"
        placeholder="sorty beer by name..."
      />
    </div>

    <div class="itemError" v-if="input && !filteredBeers().length">
      <p>No results found!</p>
    </div>

</section>

 
  <section>
    <BeersCard v-for="beer in filteredBeers()" :beer="beer"/>
  </section>
  </main>
</template>

<style lang="scss" scoped>
@import "../scss/styles.scss";


main{
  background-color: beige;
  margin: 0 ;
  display: flex;
  flex-direction: column;
  // width: 80%;
  section {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 1em;
    justify-content: center;
    align-items: center;
  }
}

</style>