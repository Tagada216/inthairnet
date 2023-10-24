<template>
  <div v-if="visible" class="card">
    <div class="data">
      <p>Nom : {{ storeData.nom }}</p>
    </div>
    <div class="data">
      <p>Adresse : {{ storeData.addresse }}</p>
    </div>
    <div>
      <button @click="emit('close')">
        <svg
          width="30px"
          height="30px"
          viewBox="0 0 24 24"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <circle cx="12" cy="12" r="10" stroke="#1C274C" stroke-width="1.5" />
          <path
            d="M14.5 9.50002L9.5 14.5M9.49998 9.5L14.5 14.5"
            stroke="#1C274C"
            stroke-width="1.5"
            stroke-linecap="round"
          />
        </svg>
      </button>
    </div>
    <a
      href="https://www.data.gouv.fr/fr/datasets/coordonnees-des-enseignes-de-coiffure-comportant-des-jeux-de-mots-cocasses-dans-leur-appellation/"
      target="_blank"
      >Dataset
    </a>
  </div>
</template>

<script setup lang="ts">
import { defineProps, defineEmits } from "vue";

defineProps({
  visible: {
    type: Boolean,
    required: false,
  },
  storeData: {
    type: Object,
  },
});

const emit = defineEmits(["close"]);
</script>

<style scoped>
.card {
  --size: clamp(300px, 600px);
  width: var(--size);
  background-color: beige;
  border-radius: 15px;
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
}
.data {
  display: flex;
  flex-direction: row;
  justify-content: center;
  font-family: "Josefin Sans", sans-serif;
}
</style>
