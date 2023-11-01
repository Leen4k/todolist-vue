<template>
  <form @submit.prevent="addItemAndClear(todo)" class="input-field">
    <!-- <input v-model="todo" type="text" /><button>add</button> -->
    
    <textarea v-model="todo" type="text" placeholder="Enter your new todo"></textarea>
    <button class="uil uil-notes note-icon"></button>
  </form>
</template>

<script>
import { ref, defineComponent } from "vue";
import { useTodoListStore } from "../stores/useTodoListStore";

export default defineComponent ({
  setup() {
    const todo = ref("");
    const store = useTodoListStore();

    function addItemAndClear(item) {
      if (todo.value.length === 0) {
        return;
      }
      store.addTodo(item);
      todo.value = "";
    }

    return { todo, addItemAndClear, store };
  }
})
</script>





