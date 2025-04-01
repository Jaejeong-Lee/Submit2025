<script setup>
import Title_todo from './components/Title_todo.vue'
import Body_todo from './components/Body_todo.vue'
import NewList_todo from './components/NewList_todo.vue'

import { onMounted, ref } from 'vue'

const todos = ref([])

const addTodo = newTodo => {
  if (!newTodo.trim()) return
  todos.value.push({
    id: Date.now(),
    text: newTodo,
    completed: false, // 체크표시 여부
    trashed: false, //쓰레기통버튼 (삭제 여부)
    finishedAt: null, //완료시간 저장
    bold: false,
  })
  saveTodo()
}
// 할일의 완료 상태 토글하는 함수(+완료 시간 기록 기능 추가)
const toggleTodo = id => {
  const todo = todos.value.find(todo => todo.id === id)
  if (todo) {
    todo.completed = !todo.completed
    // 완료 날짜가 없으면, 현재 시간으로 표시, 있으면 null로 초기화.
    todo.finishedAt = todo.finishedAt ? null : new Date().toLocaleString()
    saveTodo()
  }
}
// 할일을 완료로 표시하는 함수
// const finishedTodo = id => {
//   const todo = todos.value.find(todo => todo.id === id)
//   if (todo) {
//     // 완료 날짜가 없으면, 현재 시간으로 표시, 있으면 null로 초기화.
//     todo.finishedAt = todo.finishedAt ? null : new Date().toLocaleString()
//   }
// }
// 할일 삭제하는 쓰레기통 버튼 함수
const trashTodo = id => {
  todos.value = todos.value.filter(todo => todo.id !== id)
  // filter를 통해 쓰레기통 버튼을 누른, 즉 id가 같은 할일을 필터링(제외)하고
  // 남은 목록들만 다시 todos.value에 덮어씌워주는 역할임.
  saveTodo()

  // [Splice 함수 사용의 case]
  // const todoIndex = todos.value.findIndex(todo => todo.id === id)
  // // findIndex : 배열에서 인덱스를 찾아 값을 다시 대입해줌.
  // if (todoIndex !== -1) {
  //   todos.value.splice(todoIndex, 1) //해당 todo를 배열에서 삭제
  // }
}
// 할일 강조(bold)표시하는 함수
const boldChange = id => {
  const todo = todos.value.find(todo => todo.id === id)
  if (todo) {
    todo.bold = !todo.bold
  }
}

// 로컬스토리지 저장하는 함수(JSON형태로 바꿔주는 함수)
// 로컬스토리지는 문자열만 저장 가능하므로, JSON 문자열로 변환함.
// setItem( key값, value(저장할 데이터) )
const saveTodo = () => {
  localStorage.setItem('todos', JSON.stringify(todos.value))
}

// 로컬스토리지 데이터 호출(?) : JSON 형태를 다시 Javascript 형식으로 변환
// => parse() 사용
// getItem : 데이터 가져옴
const loadTodos = () => {
  const saveTodos = localStorage.getItem('todos')
  if (saveTodos) {
    todos.value = JSON.parse(saveTodos)
  } else {
    todos.value = [] // 데이터가 없으면 빈 배열로 초기화
  }
}
// 마운트 단계 시 데이터 출력
onMounted(() => {
  loadTodos()
})
</script>

<template>
  <section class="container">
    <header>
      <Title_todo />
    </header>
    <main>
      <ul class="items">
        <Body_todo
          v-for="todo in todos"
          :key="todo.id"
          :todo="todo"
          @toggle-todo="toggleTodo"
          @finished-todo="finishedTodo"
          @trash-todo="trashTodo"
          @bold-change="boldChange"
        />
      </ul>
    </main>
    <footer>
      <NewList_todo @add-todo="addTodo" />
    </footer>
  </section>
</template>

<style scoped></style>
