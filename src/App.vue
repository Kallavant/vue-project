<script setup>
//Parte de reactividad del curso
import { ref, reactive, computed } from "vue";

const count = ref(0);

function increment() {
  count.value++;
}

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

const awesome = ref(true);

const parentMessage = ref('Parent')
const items = ref([{ message: 'Foo' }, { message: 'Bar' }])

const myObject = reactive({
  title: 'How to do lists in Vue',
  author: 'Jane Doe',
  publishedAt: '2016-04-10'
})

const sets = ref([
  [1, 2, 3, 4, 5],
  [6, 7, 8, 9, 10]
])

function even(numbers) {
  return numbers.filter((number) => number % 2 === 0)
}
</script>

<template>
  <div class="container">
    <h1>Hola Mundo</h1>
    
    <!-- Parte Reactiva -->
    <div class="section">
      <h2>Parte Reactiva</h2>
      <p>Botón para Incrementar:</p>
      <button @click="increment" class="button">
        {{ count }}
      </button>
    </div>

    <!-- Separador -->
    <div class="separator">
      <span>&#x2193;</span>
    </div>

    <!-- Parte Computada -->
    <div class="section">
      <h2>Propiedades Computadas</h2>
      <p>Has published books:</p>
      <span>{{ publishedBooksMessage }}</span>
    </div>

    <!-- Separador -->
    <div class="separator">
      <span>&#x2193;</span>
    </div>

    <!-- Renderización Condicional -->
    <div class="section">
      <h2>Renderización Condicional</h2>
      <button @click="awesome = !awesome" class="button">Toggle</button>
      <h1 v-if="awesome">Vue is awesome!</h1>
      <h1 v-else>Oh no 😢</h1>
    </div>

    <!-- Separador -->
    <div class="separator">
      <span>&#x2193;</span>
    </div>

    <!-- Lista de la lista -->
    <div class="section">
      <h2>Lista de la Lista</h2>
      <li v-for="(item, index) in items">
  	  {{ parentMessage }} - {{ index }} - {{ item.message }}
	    </li>
      <ul>
          <li v-for="(value, key, index) in myObject">
		      {{ index }}. {{ key }}: {{ value }}
		      </li>
      </ul>
      <ul v-for="numbers in sets">
          <li v-for="n in even(numbers)">{{ n }}</li>
      </ul>
    </div>
  </div>

  
</template>

<style scoped>
.container {
  font-family: Arial, sans-serif;
  margin: 20px;
}

.section {
  border: 1px solid #ccc;
  border-radius: 8px;
  padding: 20px;
  margin-bottom: 20px;
  background-color: #f9f9f9;
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
}

.separator {
  text-align: center;
  margin: 20px 0;
  font-size: 24px;
  color: #666;
}

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

