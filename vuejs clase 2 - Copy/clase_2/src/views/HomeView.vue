<script setup>

import { ref } from 'vue';
import card from "../components/card.vue";

/* cammelcase, snakecase */

let character = ref([]);
let page = ref(1)

function nextpage() {
  page.value++;
  loadCharacters()
}

function backpage() {
  page.value--;
  loadCharacters()
}

async function loadCharacters() {
  const response = await fetch(`https://rickandmortyapi.com/api/character?page=${page.value}`);
  const data = await response.json();
  character.value = data.results;
  console.log(data);
}

loadCharacters();

</script>

<template>

  <div class="m-8" id="container">

    <div class="flex justify-center mt-10 mb-10">
      <h1 class="text-5xl text-rose-950">Rick and Morty API</h1>
    </div>

    <div class="mb-8 grid grid-cols-2 lg:grid-cols-4 gap-12 mx-auto">

      <div v-for="personaje in character" :key="character.id" class="bg-red-700 flex justify-center text-center rounded-lg  shadow-md">
        <card :character="personaje"/>
      </div>
    </div>

    <div class="flex flex-row justify-around">
      <button @click="nextpage" class="p-5 rounded-lg bg-black text-white">Go to next page</button>
      <span> {{ page }} </span>
      <button @click="backpage" :disabled="page === 1" class="p-5 rounded-lg bg-black text-white">Go to previous page</button>      
    </div>
<!-- : para condiciones especiales z para clases de css -->
  </div>


  </template>
