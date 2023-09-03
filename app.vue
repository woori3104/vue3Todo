<template>
  <div>
    <h1>Todo App</h1>
    <input v-model="newTodo" @keyup.enter="addTodo" placeholder="New Todo" />
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        {{ todo }}
        <button @click="() => removeTodo(index)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { ref } from 'vue';

export default {
  name: 'TodoApp',
  setup() {
    const newTodo = ref<string>('');
    const todos = ref<string[]>([]);

    const addTodo = () => {
      if (newTodo.value.trim() !== '') {
        todos.value.push(newTodo.value.trim());
        newTodo.value = '';
      }
    };

    const removeTodo = (index: number) => {
      todos.value.splice(index, 1);
    };

    return {
      newTodo,
      todos,
      addTodo,
      removeTodo
    };
  }
};
</script>
