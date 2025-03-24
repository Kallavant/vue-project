<script setup>
import { reactive, computed } from "vue";
// Propiedades computadas
const author = reactive({
  name: "John Doe",
  books: [
    "Vue 2 - Advanced Guide",
    "Vue 3 - Basic Guide",
    "Vue 4 - The Mystery",
  ],
});

const publishedBooksMessage = computed(() => {
  return author.books.length > 0 ? "Yes" : "No";
});
</script>

<template>
  <!-- Parte Computada -->
  <div class="section">
      <h2>Propiedades Computadas</h2>
      <p>Has published books:</p>
      <span>{{ publishedBooksMessage }}</span>
  </div>
</template>

<style scoped>

</style>
