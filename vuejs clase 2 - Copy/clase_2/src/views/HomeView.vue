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

    <div class="mb-8 grid grid-cols-2 lg:grid-cols-4 gap-12 mx-auto ">

      <div v-for="personaje in character" :key="character.id" class="bg-black flex relative hover:scale hover:transition transition justify-center text-center rounded-lg shadow-md ">
        <card :character="personaje"/>
      </div>
    </div>

    <div class="flex flex-row justify-around">

      <button @click="backpage" :disabled="page === 1" class="p-5 rounded-lg bg-black text-white hover:transition hover:bg-white hover:text-black">Go to previous page</button>      
      <span class="rounded-full bg-white self-center p-2 px-3"> {{ page }} </span>
      <button @click="nextpage" :disabled="page === 42" class="p-5 rounded-lg bg-black text-white hover:transition hover:bg-white hover:text-black">Go to next page</button>

  </div>
<!-- para condiciones especiales z para clases de css -->
  </div>


  </template>
