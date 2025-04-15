<script setup></script>

<template>
  <body>
    <section class="container">
      <!-- <header class="header"><h1>오늘의 할일</h1></header> -->

      <ul class="items">
        <li class="item">
          <span>오늘의 할일 리스트1</span>
          <i class="fa-solid fa-check"></i>
          <!-- check 아이콘 -->
          <i class="fa-solid fa-trash-can"></i>
          <!-- 쓰레기통 아이콘 -->
        </li>
        <li class="item">
          <span>오늘의 할일 리스트1</span>
          <i class="fa-solid fa-check"></i>
          <i class="fa-solid fa-trash-can"></i>
        </li>
      </ul>
    </section>
  </body>
</template>

<style scoped>
/* * {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
li {
  list-style: none;
} */

/* 이 위쪽은 reset역할임 */

body {
  background-color: #ced3df;
}
</style>
