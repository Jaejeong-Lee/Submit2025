<script setup>
// defineProps (컴포지션 API 방법에서 씀.
// 옵션 방식: 그냥 Props)
// 부모 컴포넌트에서 전달'받은' 프로퍼티를 정의하는 함수
defineProps(['name', 'checked']);
</script>

<template>
  <li><input type="checkbox" :checked="checked" />{{ name }}</li>
</template>

<style scoped></style>
