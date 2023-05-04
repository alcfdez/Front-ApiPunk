<script setup>
import { defineProps } from 'vue';

const props = defineProps ({
    beer : Object,
});



</script>

<template>

<div class="card">
    <p class="card-name">{{  beer.name }}</p>
    <img  class="card-img"  :src="beer.image_url" alt="beer image"/>

    <!-- <p class="card-tagline" > Tagline: {{  beer.tagline }} </p>
    <p class="card-description">Description: {{ beer.description }} </p> -->
</div>





  
<!-- 
<div class="beerContainer" v-for="beer in beers" :key="beer.id">
    <div class="beerCard">
        <img class="beerImg" v-bind:src="beer.image_url" alt="Beer Image"/>
        <div class="bodyCard">
            <h3 class="beerName"> {{ beer.name }}</h3>
            <p><strong>Tagline:</strong> {{ beer.tagline }}</p>
            <p><strong>Description:</strong> {{ beer.description }}</p>

        </div>

    </div>

</div> -->




</template>

<style lang="scss">

.card{
    margin: 0;
    margin-bottom: 5em;
    width: 15em;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
		color: black;
		padding: 0.5em;
		text-align: center;
		border: 1px solid rgba(163, 153, 163, 0.3);
		-webkit-box-shadow: 0px 6px 6px 0px rgba(163, 153, 163, 1);
		-moz-box-shadow: 0px 6px 6px 0px rgba(163, 153, 163, 1);
		box-shadow: 0px 6px 6px 0px rgba(163, 153, 163, 1);
	
		&__title {
			position: relative;
			bottom: 50px;
			font-size: 1em;
		}

		&__author {
			position: relative;
			bottom: 45px;
			font-size: 0.8em;
			color: grey;
		}

		&__img {
			border-radius: 50%;
			width: 50%;
			height: 70%;
			position: relative;
			bottom: 65px;
		}
	}


/* main{
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    gap: 1em;
    justify-content: center;
    align-items: center;

}

.beerContainer{
    display: flex;
    flex-direction: row;
    

}
.beerCard{
    background-color: rgb(177, 189, 190);
    margin:0 auto;
    margin-bottom: 5em;
    width: 15em;
    display: flex;
    flex-direction: column; 
    justify-content: center;
    align-items: center;
    color: rgb(23, 23, 23);
    padding: 0.5em;
    text-align: center;
    border-radius: 5%;
    border: 1px solid  rgb(156, 185, 188);
    }

.beerImg{
    width: 40%;
    height: 60%;
}

.beerName{
    font-size: large;
    font-weight: 900;
} */


 </style>
