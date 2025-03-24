<script setup>
//Parte de reactividad del curso
import { ref, reactive, computed, watch } from "vue";
import ReactividadFundamental from "./components/ReactividadFundamental.vue";
import ParteComputada from "./components/ParteComputada.vue";
import Condicional from "./components/Condicional.vue";
import Listas from "./components/Listas.vue";
import Eventos from "./components/Eventos.vue";
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
    <Listas />

    <!-- Separador -->
    <div class="separator">
      <span>&#x2193;</span>
    </div>

    <!-- Eventos -->
    <Eventos />

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
