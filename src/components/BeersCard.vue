<script>
import { onMounted } from 'vue';
import axios from 'axios';


export default{
    setup () { 

       const beers = [];

        const fetchData = async () => {
            const response = await axios.get('https://api.punkapi.com/v2/beers/');
            beers.push(...response.data);
            // console.log(beers);
            console.log(response.data);
        };

        onMounted(fetchData);

        return{
            beers,
        };
    }
}




</script>

<template>

  


<main>

<div class="beerContainer" v-for="beer in beers" :key="beer.id">
    <div class="beerCard">
        <img class="beerImg" v-bind:src="beer.image_url" alt="Beer Image"/>
        <div class="bodyCard">
            <h3 class="beerName"> {{ beer.name }}</h3>
            <p><strong>Tagline:</strong> {{ beer.tagline }}</p>
            <p><strong>Description:</strong> {{ beer.description }}</p>

        </div>

    </div>

</div>

</main>

<!-- <div id="firstDiv"> -->
 <!-- <div v-if="beers.length" id="secondDiv"> -->
        <!-- <div v-for="beer in beers" :key="beer.id" class="card">
            <div style="display: inline-block; padding: 16px; margin: 16px;">
                <img :src="beer.image_url" alt="Beer Image" class="beerImg">
                <h3 class="beerName">{{ beer.name }}</h3>
                <p>Tagline: {{ beer.tagline }}</p>
                <p>Description: {{ beer.description }}</p>

            </div>
    
    
        </div> -->
    <!-- </div> -->
<!-- </div> -->

</template>

<style>

main{
    display: grid;
    grid-template-columns: repeat(4, 1fr);
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
}


 </style>
