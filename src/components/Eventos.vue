<script setup>
import { ref } from "vue";
// Evento
const counter = ref(0);
const name = ref("Vue.js");

function greet(event) {
  alert(`Hello ${name.value}!`);
  // `event` is the native DOM event
  if (event) {
    alert(event.target.tagName);
  }
}

function say(message) {
  alert(message);
}

function warn(message, event) {
  // now we have access to the native event
  if (event) {
    event.preventDefault();
  }
  alert(message);
}
</script>

<template>
    <div class="section">
      <h2>Eventos</h2>
      <button @click="counter++">Add 1</button>
      <p>The button above has been clicked {{ counter }} times.</p>
      <p>Manecles de método</p>
      <button @click="greet">Greet</button>
      <p>Llamando a Métodos en Manecles en Línea</p>
      <button @click="say('hello')">Say hello</button>
      <button @click="say('bye')">Say bye</button>
      <p>Acceder a evento argumentación en Manecles Inline</p>
      <!-- using $event special variable -->
      <button @click="warn('Form cannot be submitted yet.', $event)">
        Submit
      </button>
      <!-- using inline arrow function -->
      <button @click="(event) => warn('Form cannot be submitted yet.', event)">
        Submit
      </button>
    </div>
</template>