<script setup>
import { ref, watch } from 'vue';

const x = ref(0);
const result = ref(0);

watch(x, (current, old) => {
  console.log(`바뀌기 전 : ${old} => 바뀐 후: ${current}`);
  result.value = current;
});
</script>

<template>
  <div>
    X : <input type="text" v-model.number="x" />
    <br />
    <div>결과 : {{ result }}</div>
  </div>
</template>

<style scoped></style>
