<script setup>
import { ref } from 'vue'

const emit = defineEmits(['add-todo'])

const newTodo = ref('')
const addTodo = () => {
  if (newTodo.value.trim === '') {
    return
  }
  emit('add-todo', newTodo.value)
  newTodo.value = ''
}
</script>

<template>
  <footer class="footer">
    <input @keyup.enter="addTodo" v-model="newTodo" type="text" class="footer_input" />
    <i @click="addTodo" class="fa-solid fa-plus"></i>
  </footer>
</template>

<style scoped></style>
