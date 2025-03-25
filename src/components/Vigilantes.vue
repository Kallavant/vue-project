<script setup>
import { ref, watch } from "vue";

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
    <!-- Vigilantes -->
    <div class="section">
      <h2>Vigilantes</h2>
      <p>
        Ask a yes/no question:
        <input v-model="question" :disabled="loading" />
      </p>
      <p>{{ answer }}</p>
    </div>

</template>