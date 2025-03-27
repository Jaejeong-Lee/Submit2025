<script setup>
// defineProps (컴포지션 방법에서 씀. 옵션 방식은 그냥 Props)
// 부모 컴포넌트에서 전달'받은' 프로퍼티를 정의하는 함수
defineProps({
  // validator
  // Vue 공식기능
  // 부모가 prop을 전달할 때마다 함수가 호출됨

  idol: {
    type: Object,
    required: true,
    validator: (value) => {
      return (
        (typeof value.id === 'number' || typeof value.id === 'string') &&
        typeof value.name === 'string' &&
        typeof value.checked === 'boolean'
      );
    },
  },
});
</script>

<template>
  <li><input type="checkbox" :checked="idol.checked" />{{ idol.name }}</li>
</template>

<style scoped></style>
