<script setup>
import { defineProps } from "vue";

const props = defineProps({
  beer: Object,
});
</script>

<template>
  <div class="card">
    <p class="card-name">{{ beer.name }}</p>
    <img class="card-img" :src="beer.image_url" alt="beer image" />
    <p class="card-tagline">{{ beer.tagline }}</p>
  </div>
</template>

<style lang="scss" scoped>
@import "../scss/styles.scss";
.card {
  margin-bottom: 5em;
  width: 15em;
  height: 20em;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 0.5em;
  text-align: center;
  border: 1px solid rgba(163, 153, 163, 0.3);
  box-shadow: 0px 6px 6px 0px rgba(163, 153, 163, 1);

  &-name {
    margin-bottom: 5%;
    font-family: $font-beer;
    font-size: 1em;
  }

  &-img {
    width: 30%;
    height: 60%;
  }

  &-tagline{
    margin-top: 5%;
    font-family: $font-text;
  }
}

</style>
