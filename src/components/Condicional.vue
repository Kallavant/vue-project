<script setup>
import { ref } from "vue";
const awesome = ref(true);
</script>

<template>
  <!-- Parte Reactiva -->
  <div class="section">
      <h2>Renderización Condicional</h2>
      <button @click="awesome = !awesome" class="button">Toggle</button>
      <h1 v-if="awesome">Vue is awesome!</h1>
      <h1 v-else>Oh no 😢</h1>
  </div>

</template>

<style scoped>

.button {
  padding: 10px 20px;
  border: none;
  background-color: #42b883;
  color: white;
  font-size: 16px;
  cursor: pointer;
  border-radius: 5px;
}
.button:hover {
  background-color: #38a169;
}

</style>
