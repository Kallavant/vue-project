<script setup>
import { ref } from "vue";
const count = ref(0);

function increment() {
  count.value++;
}
</script>

<template>
  <!-- Parte Reactiva -->
  <div class="section">
    <h2>Parte Reactiva</h2>
    <p>Botón para Incrementar:</p>
    <button @click="increment" class="button">
      {{ count }}
    </button>
  </div>
</template>

<style scoped>

</style>
