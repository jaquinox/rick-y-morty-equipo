<template>
    hola
</template>


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
