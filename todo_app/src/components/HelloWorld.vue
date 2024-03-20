<template>
  <div class="todo-app">
    <h1>{{ title }}</h1>
    <input type="text" v-model="newTodo" @keyup.enter="addTodo" placeholder="Add new todo"
      class="w-full p-2 border border-gray-300 rounded mb-4">
    <ul>
      <li v-for="(todo, index) in todos" :key="index" class="flex items-center justify-between bg-white border border-gray-300 p-4 mb-2">
        <input type="checkbox" v-model="todo.completed" class="mr-2">
        <span :class="{ 'line-through': todo.completed }">{{ todo.text }}</span>
        <button @click="removeTodo(index)" class="text-red-600">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'TodoApp',
  data() {
    return {
      title: 'Vue Todo App',
      newTodo: '',
      todos: []
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== '') {
        this.todos.push({
          text: this.newTodo,
          completed: false
        });
        this.newTodo = '';
      }
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    }
  }
}
</script>

<style scoped>
.todo-app {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  background-color: #fff;
  border-radius: 5px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

h1 {
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 20px;
}

ul {
  padding: 0;
  list-style: none;
}

li {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

input[type="checkbox"] {
  margin-right: 10px;
}

.line-through {
  text-decoration: line-through;
}

button {
  background-color: transparent;
  border: none;
  cursor: pointer;
}
</style>
