<script setup>
import { ref} from "vue";
// Encuadernaciones de entrada
const message = ref("");
const message2 = ref("");
const checked = ref(true);
const checkedNames = ref([]);
const picked = ref("One");
const selected = ref("");
const selected2 = ref([]);
</script>

<template>
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

</template>

<style scoped>
select[multiple] {
  width: 100px;
}
</style>
