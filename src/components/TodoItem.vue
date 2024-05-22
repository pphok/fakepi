<template>
  <div v-if="todo">
    <h1>{{ todo.title }}</h1>
    <p>User ID: {{ todo.userId }}</p>
    <p>Completed: {{ todo.completed }}</p>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      todo: null
    };
  },
  created() {
    this.fetchTodo();
  },
  methods: {
    async fetchTodo() {
      try {
        const response = await axios.get('https://jsonplaceholder.typicode.com/todos/1');
        this.todo = response.data;
      } catch (error) {
        console.error('Error fetching the todo item:', error);
      }
    }
  }
};
</script>

<style scoped>
h1 {
  font-size: 24px;
}
p {
  font-size: 18px;
}
</style>
