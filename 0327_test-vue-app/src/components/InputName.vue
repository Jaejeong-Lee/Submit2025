<script setup>
//컴포지션 방식
// emit : 자식이 부모에게 이벤트 전달!
const emit = defineEmits(['nameChange']);

import { ref } from 'vue';
const childName = ref('');
</script>

<template>
  <div>
    이름: <input type="text" v-model="childName" />
    <button @click="emit('nameChange', { childName })">이벤트발신</button>
  </div>
</template>

<style scoped></style>
