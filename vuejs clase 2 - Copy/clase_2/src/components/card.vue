<script setup>


import { defineProps } from 'vue'; 
    const props = defineProps({
        character: {
            require: true,
            type: Object
     } 
    })

</script>

<template>
    
    <div class="flex-col border-4 border-black hover:scale-110 hover:transition transition">

        <div>
        
            <img :src="character.image" alt="Image" class="p-5 bg-zinc-600 h-full">
        
        </div>
        
        <div class="text-3xl snap-center h-20 bg-slate-500 flex-col flex justify-center">

            <h3>{{character.name}}</h3>

        </div>

    </div>
    
</template>
