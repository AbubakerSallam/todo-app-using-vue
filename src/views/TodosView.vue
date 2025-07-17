<script setup>
import { computed, ref, watch } from 'vue';
import { uid } from 'uid';
import { Icon } from '@iconify/vue';

import TodoCreator from '@/components/TodoCreator.vue';
import TodoItem from '@/components/TodoItem.vue';
const todoList = ref([]);

watch(todoList, () => {
  saveTodoListToLocalStorage();
}, {
  deep: true,
});
const feachTodoList = () => {
  const savedTodoList = JSON.parse(localStorage.getItem("todoList"));
  if (savedTodoList) {
    todoList.value = savedTodoList;
  }
}
const todoCompleted = computed(() => {
  return todoList.value.every((todo) => todo.isCompleted);
});
feachTodoList();

const saveTodoListToLocalStorage = () => {
  localStorage.setItem("todoList", JSON.stringify(todoList.value));
}
const createTodo = (todo) => {
  todoList.value.push({
    id: uid(),
    todo,
    isCompleted: null,
    isEditing: null,
  });
}

const toggleComplete = (todoPos) => {
  todoList.value[todoPos].isCompleted = !todoList.value[todoPos].isCompleted;
}
const toggleEditTodo = (todoPos) => {
  todoList.value[todoPos].isEditing = !todoList.value[todoPos].isEditing;
}
const updateTodo = (todoVal, todoPos) => {
  todoList.value[todoPos].todo = todoVal;
}
const deleteTodo = (todoId) => {
  todoList.value = todoList.value.filter((todo) => todo.id !== todoId);
}
</script>

<template>
  <main>
    <h1>انشاء مهمة</h1>
    <TodoCreator @create-todo="createTodo" />

    <ul class="todo-list" v-if="todoList.length > 0">
      <TodoItem v-for="(todo, index) in todoList" :todo="todo" :index="index" @toggle-complete="toggleComplete"
        @edit-todo="toggleEditTodo" @update-todo="updateTodo" @delete-todo="deleteTodo" />
    </ul>
    <p class="todos-msg" v-else>
      <span>ليس لديك اي مهمات حتى الان! اضف مهامك</span>
      <Icon class="icon" icon="noto-v1:sad-but-relieved-face" color="#41n080" width="22" />

    </p>
    <p v-if="todoCompleted && todoList.length > 0" class="todos-msg">
      <span>تهانينا , اكملت جميع المهام ! </span>
      <Icon class="icon" icon="noto-v1:party-popper" />

    </p>
  </main>
</template>



<style lang="scss" scoped>
main {
  display: flex;
  flex-direction: column;
  max-width: 500px;
  width: 100%;
  margin: 0 auto;
  padding: 20px 16px;

  h1 {
    margin-bottom: 10px;
    text-align: center;
  }

}
.todos-msg{
  text-align: center;
}
</style>
