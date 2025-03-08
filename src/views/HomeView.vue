<script setup lang="ts" >


    const characters= [       {
            "id": 1,
            "name": "Rick Sanchez",
            "status": "Alive",
            "species": "Human",
            "type": "",
            "gender": "Male",
            "origin": {
                "name": "Earth (C-137)",
                "url": "https://rickandmortyapi.com/api/location/1"
            },
            "location": {
                "name": "Citadel of Ricks",
                "url": "https://rickandmortyapi.com/api/location/3"
            },
            "image": "https://rickandmortyapi.com/api/character/avatar/1.jpeg",        
            "url": "https://rickandmortyapi.com/api/character/1",
            "created": "2017-11-04T18:48:46.250Z"
        },
        {
            "id": 2,
            "name": "Morty Smith",
            "status": "Alive",
            "species": "Human",
            "type": "",
            "gender": "Male",
            "origin": {
                "name": "unknown",
                "url": ""
            },
            "location": {
                "name": "Citadel of Ricks",
                "url": "https://rickandmortyapi.com/api/location/3"
            },
            "image": "https://rickandmortyapi.com/api/character/avatar/2.jpeg",
            "url": "https://rickandmortyapi.com/api/character/2",
            "created": "2017-11-04T18:50:21.651Z"
        },

]


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