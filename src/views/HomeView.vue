


<script setup lang="ts">

import { onMounted, ref, computed } from 'vue'

const page = ref<number>(1)

const nextPage = ref<string>('')

const characters = ref([])

const loadCharacters = async () => {
    const response = await fetch(`https://rickandmortyapi.com/api/character?page=${page.value}`)
    const data = await response.json()
    characters.value = data.results
    console.log(characters.value)
}


onMounted(() => {
  loadCharacters()
})

const incrementPage = () => {
  if (nextPage.value !== null) {
    page.value++
    loadCharacters()
  }

}


const decrementPage = () => {
  if (page.value > 1) {
    page.value--
    loadCharacters()
  } else {
    page.value = 1
    loadCharacters()
  }
}


</script>



<template>

<div class="flex justify-center mt-5">
      <button
        @click="decrementPage"
        class="me-5 rounded-md bg-orange-800 px-10.5 py-2.5 text-sm size-30 text-white shadow-xs"
      >
        <span class="text-5xl font-extrabold">-</span>
      </button>

      <p class="text-5xl font-extrabold">Página: {{ page }}</p>

      <button
        @click="incrementPage"
        class="ms-5 rounded-md bg-indigo-600 px-10.5 py-2.5 text-sm size-30 text-white shadow-xs"
      >
        <span class="text-5xl font-extrabold">+</span>
      </button>
</div>

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