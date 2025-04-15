<script setup>
// defineProps (컴포지션 방법에서 씀. 옵션 방식은 그냥 Props)
// 부모 컴포넌트에서 전달'받은' 프로퍼티를 정의하는 함수
defineProps(['idol']); // 부모에서 :idol ="idol" 중 왼쪽 idol(속성명)을 의미
</script>

<template>
  <li><input type="checkbox" :checked="idol.checked" />{{ idol.name }}</li>
</template>

<style scoped></style>
