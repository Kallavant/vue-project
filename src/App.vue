<script setup>
//Parte de reactividad del curso
import { ref, reactive, computed, watch } from "vue";
import ReactividadFundamental from "./components/ReactividadFundamental.vue";
import ParteComputada from "./components/ParteComputada.vue";
import Condicional from "./components/Condicional.vue";
import Listas from "./components/Listas.vue";
import Eventos from "./components/Eventos.vue";
import Encuadernaciones from "./components/Encuadernaciones.vue";
import Vigilantes from "./components/Vigilantes.vue";
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
    <Encuadernaciones />

    <!-- Separador -->
    <div class="separator">
      <span>&#x2193;</span>
    </div>

    <!-- Vigilantes -->
    <Vigilantes />
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

</style>
