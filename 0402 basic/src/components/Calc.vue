<script setup>
const x = 10; // 10 으로 초기화
const y = 20; // 20 으로 초기화
</script>

<template>
  <div>
    X : <input type="text" v-model.number="x" />
    <br />
    Y : <input type="text" v-model.number="y" />
    <br />
  </div>
</template>

<style scoped></style>
