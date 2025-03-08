


<script setup lang="ts">

import { onMounted, ref, computed } from 'vue'


const characters = ref([])

const loadCharacters = async () => {
  const response = await fetch(`https://rickandmortyapi.com/api/character`)
  const data = await response.json()
    characters.value = data.results
    console.log(characters.value)
}


onMounted(() => {
  loadCharacters()
})


</script>



<template>

    <div>
        <h1>Personajes</h1>
        <div class="grid grid-cols-3 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 text-center">
            <div v-for="character in characters" :key="character.id" >
                <div >
                    <h2>{{ character.name }}</h2>
                    <img :src="character.image" alt="Imagen del personaje">
                    <p>Estado: {{ character.status }}</p>
                    <p>Especie: {{ character.species }}</p>
                    <p>Género: {{ character.gender }}</p>
                    <p>Origen: {{ character.origin.name }}</p>
                    <p>Ubicación: {{ character.location.name }}</p>
                </div>
            </div>
        </div>
    </div>

</template>




<style>




</style>