<script setup>
//Parte de reactividad del curso
import { ref, reactive, computed, watch } from "vue";
import ReactividadFundamental from "./components/ReactividadFundamental.vue";
import ParteComputada from "./components/ParteComputada.vue";
import Condicional from "./components/Condicional.vue";
// Lista de la lista
const parentMessage = ref("Parent");
const items = ref([{ message: "Foo" }, { message: "Bar" }]);

const myObject = reactive({
  title: "How to do lists in Vue",
  author: "Jane Doe",
  publishedAt: "2016-04-10",
});

const sets = ref([
  [1, 2, 3, 4, 5],
  [6, 7, 8, 9, 10],
]);

function even(numbers) {
  return numbers.filter((number) => number % 2 === 0);
}
//********************************************************************************
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
//********************************************************************************
// Encuadernaciones de entrada
const message = ref("");
const message2 = ref("");
const checked = ref(true);
const checkedNames = ref([]);
const picked = ref("One");
const selected = ref("");
const selected2 = ref([]);
//********************************************************************************
//Vigilantes
const question = ref("");
const answer = ref("Questions usually contain a question mark. ;-)");
const loading = ref(false);

// watch works directly on a ref
watch(question, async (newQuestion, oldQuestion) => {
  if (newQuestion.includes("?")) {
    loading.value = true;
    answer.value = "Thinking...";
    try {
      const res = await fetch("https://yesno.wtf/api");
      answer.value = (await res.json()).answer;
    } catch (error) {
      answer.value = "Error! Could not reach the API. " + error;
    } finally {
      loading.value = false;
    }
  }
});
</script>

<template>
  <div class="container">
    <h1>Hola Mundo</h1>

    <!-- Parte Reactiva -->
     <ReactividadFundamental />
  
    <!-- Separador -->
    <div class="separator">
      <span>&#x2193;</span>
    </div>

    <!-- Parte Computada -->
    <ParteComputada />

    <!-- Separador -->
    <div class="separator">
      <span>&#x2193;</span>
    </div>

    <!-- Renderización Condicional -->
    <Condicional />

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

    <!-- Separador -->
    <div class="separator">
      <span>&#x2193;</span>
    </div>

    <!-- Eventos -->
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

    <!-- Separador -->
    <div class="separator">
      <span>&#x2193;</span>
    </div>

    <!-- Forma Encuadernaciones de entrada -->
    <div class="section">
      <h2>Forma Encuadernaciones de entrada</h2>
      <p>Message is: {{ message }}</p>
      <input v-model="message" placeholder="edit me" />
      <p>Texto multilínea</p>
      <span>Multiline message is:</span>
      <p style="white-space: pre-line">{{ message2 }}</p>
      <textarea v-model="message2" placeholder="add multiple lines"></textarea>
      <p>Caja de verificación</p>
      <input type="checkbox" id="checkbox" v-model="checked" />
      <label for="checkbox">{{ checked }}</label>
      <p>Checkbox</p>
      <div>Checked names: {{ checkedNames }}</div>
      <input type="checkbox" id="jack" value="Jack" v-model="checkedNames" />
      <label for="jack">Jack</label>
      <input type="checkbox" id="john" value="John" v-model="checkedNames" />
      <label for="john">John</label>
      <input type="checkbox" id="mike" value="Mike" v-model="checkedNames" />
      <label for="mike">Mike</label>
      <p>Radio</p>
      <div>Picked: {{ picked }}</div>
      <input type="radio" id="one" value="One" v-model="picked" />
      <label for="one">One</label>
      <input type="radio" id="two" value="Two" v-model="picked" />
      <label for="two">Two</label>
      <p>Selecion</p>
      <span> Selected: {{ selected }}</span>
      <select v-model="selected">
        <option disabled value="">Please select one</option>
        <option>A</option>
        <option>B</option>
        <option>C</option>
      </select>
      <p>Array</p>
      <div>Selected: {{ selected2 }}</div>
      <select v-model="selected2" multiple>
        <option>A</option>
        <option>B</option>
        <option>C</option>
      </select>
    </div>

    <!-- Separador -->
    <div class="separator">
      <span>&#x2193;</span>
    </div>

    <!-- Vigilantes -->
    <div class="section">
      <h2>Vigilantes</h2>
      <p>
        Ask a yes/no question:
        <input v-model="question" :disabled="loading" />
      </p>
      <p>{{ answer }}</p>
    </div>
  </div>
</template>

<style scoped>
select[multiple] {
  width: 100px;
}
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

</style>
