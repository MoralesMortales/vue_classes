<script setup>

import { ref } from 'vue';
import card from "../components/card.vue";

/* cammelcase, snakecase */

let character = ref([]);

async function loadCharacters(){
  const response = await fetch(`https://rickandmortyapi.com/api/character?page=1`);
  const data = await response.json();
  character.value = data.results;
  console.log(data);
}

loadCharacters();

</script>

<template>
    <div class="flex justify-center  mt-10">
      <h1 class="text-5xl text-rose-950">Rick and Morty API</h1>
    </div>

    <br><br>

    <div v-for="personaje in character" :key="character.id">{{ 
    personaje.name }}
   </div>
    
<card/>

</template>
