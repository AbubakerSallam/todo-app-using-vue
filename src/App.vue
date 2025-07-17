<script setup>
import { RouterView } from 'vue-router'
import TodoHeader from './components/TodoHeader.vue';
</script>

<template>
 <TodoHeader/> 
  <RouterView />
</template>

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Playpen+Sans+Arabic:wght@100..800&display=swap');

*{
  font-family: 'Playpen Sans Arabic', Courier, monospace;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.container{
  max-width: 1100px;
  margin: 0 auto;
}
</style>
