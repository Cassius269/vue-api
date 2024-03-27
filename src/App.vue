<script setup lang="ts">
import { ref, type Ref } from "vue"; // importation de la méthode ref() pour la création de variables

interface character {
  name: String,
  imageUrl: String,
  createdAt: String,
}

const localCharacters : Ref<character[]>= ref([])
async function afficherFilms() {
  const response = await fetch("https://api.disneyapi.dev/character");
  const characters = await response.json();
  localCharacters.value = characters.data;
}

afficherFilms();

console.log(localCharacters.value)
</script>

<template>
  <h1>Révision de la consommation d'API</h1>
  <h2>Liste des films</h2>
  <ul>
    <li v-for="character in localCharacters">{{ character.name }}</li>
  </ul>
</template>

<style scoped>

</style>
