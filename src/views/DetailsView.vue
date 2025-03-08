<template>
 hola
  </template>
  
  <script setup lang="ts">
  import { ref, onMounted } from 'vue';
  import { useRoute } from 'vue-router';
  import type { Character } from '@/types/character'
  
  
  const route = useRoute()
  const id = route.params.id
  const character = ref()
  
  
  const loadCharacters = async () => {
    const response = await fetch(`https://rickandmortyapi.com/api/character/${id}`)
    const data = await response.json()
    character.value = data
    console.log(character.value)
    console.log(data)
    character.value = data
  }
  
  onMounted(()=>{
      loadCharacters()
  })
  </script>