<script setup>
// defineProps (컴포지션 방법에서 씀. 옵션 방식은 그냥 Props)
// 부모 컴포넌트에서 전달'받은' 프로퍼티를 정의하는 함수
defineProps({
  id: [Number, String], //문자열과 숫자형만 가능
  name: String,
  checked: {
    type: Boolean, //불리언 타입만 가능
    // default: false,
    // required: true, //필수값 설정, required는 기본적으로 true
  },
});
</script>

<template>
  <li><input type="checkbox" :checked="idol.checked" />{{ idol.name }}</li>
</template>

<style scoped></style>
