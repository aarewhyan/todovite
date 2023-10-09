<template>
  <div>
    <ul>
      <li v-for="todo in todos" :key="todo">{{ todo }}</li>
    </ul>
    <form @submit.prevent="addTodo">
      <input v-model="todoText" placeholder="What needs to be done?" />
      <button type="submit">Add Todo</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      todos: [],
      todoText: "", // Correct the variable name here (todoTest -> todoText)
    };
  },
  methods: {
    addTodo() {
      this.todos = [...this.todos, this.todoText]; // Correct the assignment here
      localStorage.setItem("todos", JSON.stringify(this.todos));
      this.todoText = ""; // Clear the input field after adding a todo
    },
  },
  mounted() {
    const existingTodos = localStorage.getItem("todos");
    this.todos = JSON.parse(existingTodos) || [];
  },
};
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
</style>