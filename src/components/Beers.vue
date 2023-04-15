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

  

<div id="firstDiv">
 <!-- <div v-if="beers.length" id="secondDiv"> -->
        <div v-for="beer in beers" :key="beer.id" class="card">
            <div style="display: inline-block; padding: 16px; margin: 16px;">
                <img :src="beer.image_url" alt="Beer Image" class="beerImg">
                <h3 class="beerName">{{ beer.name }}</h3>
                <p>Tagline: {{ beer.tagline }}</p>
                <p>Description: {{ beer.description }}</p>

            </div>
    
    
        </div>
    <!-- </div> -->
</div>


  
</template>

<style>
 </style>
