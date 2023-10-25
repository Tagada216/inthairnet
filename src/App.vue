<script setup lang="ts">
import CardStoreComponent from "./components/CardStoreComponent.vue";
import { ref, onBeforeMount } from "vue";
import { storesData } from "./store";

let displayInformations = ref(false);

const stores = storesData.features;
let selectedStore = ref();

function loadStore() {
  const index = Math.floor(Math.random() * stores.length);
  selectedStore.value = stores[index].properties;
}

onBeforeMount(() => {
  loadStore();
});
</script>

<template>
  <div class="container">
    <h1 id="magasinNom">{{ selectedStore.nom }}</h1>
    <h2 id="magasinVille">{{ selectedStore.ville }}</h2>
    <CardStoreComponent
      :visible="displayInformations"
      :storeData="selectedStore"
      @close="displayInformations = false"
    />
  </div>
  <button
    v-if="!displayInformations"
    class="more_button"
    @click="displayInformations = !displayInformations"
  >
    Voir plus
  </button>
  <button class="more_button" @click="loadStore">Nouveau nom</button>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 100%;
  height: 100%;
}
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
#magasinNom {
  font-size: 3.2em;
  color: #dbdbe3;
  text-decoration: inherit;
  font-family: "Josefin Sans", sans-serif;
  animation: flottaison 3s infinite;
}
#magasinVille {
  color: #dbdbe3;
  text-decoration: inherit;
  font-family: "Josefin Sans", sans-serif;
}
@keyframes flottaison {
  0% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-20px);
  }
  100% {
    transform: translateY(0);
  }
}
.more_button {
  font-size: 1.5rem;
  font-family: "Pacifico", cursive;
}
</style>
