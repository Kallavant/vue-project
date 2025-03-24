<script setup>
import { ref, reactive} from "vue";
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
</script>

<template>
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
</template>

<style scoped>
</style>