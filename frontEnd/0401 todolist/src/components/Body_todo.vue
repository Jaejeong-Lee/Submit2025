<script setup>
import { defineProps, defineEmits } from 'vue'

const props = defineProps({
  todo: {
    type: Object,
    required: true,
  },
})
const emit = defineEmits([
  'toggle-todo',
  'trash-todo',
  'finished-todo',
  'bold-change',
])
// 할일 완료 상태 토글하는 함수
const toggleTodo = () => {
  emit('toggle-todo', props.todo.id)
}
// 할일 삭제하는 함수
const trashTodo = () => {
  emit('trash-todo', props.todo.id)
}
// 할일 완료상태로 바꾸는 함수
// const finishedTodo = () => {
//   emit('finished-todo', props.todo.id)
// }

// 두 함수를 하나로 묶는 함수
// const handleTodoClick = () => {
//   toggleTodo()
//   finishedTodo()
// }
// 할일 강조(bold)표시하는 함수
const boldChange = () => {
  emit('bold-change', props.todo.id)
}
</script>

<template>
  <li
    class="item"
    :class="{ item_done: todo.completed, item_trashed: todo.trashed }"
  >
    <span
      class="content"
      @click.stop="boldChange"
      :class="{ boldChange: todo.bold }"
    >
      {{ todo.text }}
    </span>
    <br />
    <span class="finish" v-if="todo.finishedAt"
      >완료: {{ todo.finishedAt }}
    </span>

    <!-- check 아이콘 -->
    <i class="fa-solid fa-check" @click="toggleTodo"></i>
    <!-- 쓰레기통 아이콘 -->
    <!-- 쓰레기통 버튼 클릭 시 부모에게 삭제 요청  -->
    <i class="fa-solid fa-trash-can" @click="trashTodo"></i>
  </li>
</template>

<style scoped>
.finish {
  color: brown;
  font-style: italic;
}
.boldChange {
  font-size: 25px;
  font-weight: bold;
  color: green;
}
</style>
