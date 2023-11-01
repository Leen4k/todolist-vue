<template>
  <div class="container">
    <AddTodo />
    <TodoLists />
    <div class="pending-tasks">
      <span>You have <span v-if="!todoList.length" class="pending-num"> no </span> <span v-else class="pending-num"> {{ todoList.length }}</span> tasks pending.</span>
      <button @click="clearTodo" class="clear-button">Clear All</button>
    </div>
  </div>
</template>

<script>
import AddTodo from "./components/AddTodo.vue";
import TodoLists from "./components/TodoList.vue";
import { useTodoListStore } from "./stores/useTodoListStore";
import { storeToRefs } from "pinia";

export default {
  name: "App",
  components: {
    AddTodo,
    TodoLists,
  },
  setup (){
    const store = useTodoListStore();
    const { todoList } = storeToRefs(store);
    const {clearTodo} = store;
    return {todoList, clearTodo};
  }
};
</script>
<style>
@import "https://unicons.iconscout.com/release/v4.0.0/css/line.css";
</style>
