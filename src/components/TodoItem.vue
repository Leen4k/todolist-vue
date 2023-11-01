<template>
  <li v-for="todo in todoList" :key="todo.id" class="list pending">
    <input v-model="todo.completed" @click="toggleCompleted(todo.id)" type="checkbox" />
    <span class="task">{{ todo.item }}</span>
    <i @click="deleteTodo(todo.id)" class="uil uil-trash"></i>
  </li>
</template>

<script>
  import { defineComponent } from 'vue';
  import { useTodoListStore } from '../stores/useTodoListStore';
  import { storeToRefs } from 'pinia';
  export default defineComponent ({
    setup(){
      const store = useTodoListStore();
      const {todoList} = storeToRefs(store);
      const { toggleCompleted, deleteTodo } = store;
      return {todoList, toggleCompleted, deleteTodo};
    }
  })
</script>
