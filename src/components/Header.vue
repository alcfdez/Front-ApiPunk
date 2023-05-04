<script></script>

<template>
  <header>
    <h1>ALL BEERS YOU WANT</h1>
  </header>
</template>

<style lang="scss" scoped>
@import "../scss/styles.scss";

header {
  background-image: url("../assets/img/background-beer.avif");
  background-size: cover;
  background-repeat: no-repeat;
  width: 100%;
  height: 3em;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: $font-rubik;
  font-weight: 500;
  font-size: 2.5em;
  color: $brown;


  @media(max-width: 450px){
    font-size: 1.5em;
  }

}
</style>
