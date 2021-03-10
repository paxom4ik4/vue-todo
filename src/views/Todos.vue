<template>
  <div>
    <Header />
    <AddTodo @add-todo="addTodo" />
    <select v-model="filter">
      <option value="all">All</option>
      <option value="completed">Completed</option>
      <option value="not-completed">Not Completed</option>
    </select>
    <TodoList
      v-bind:todos="filteredTodos"
      @remove-todo="removeTodo"
      v-if="todos.length"
    />
    <p v-else>No Todos</p>
  </div>
</template>

<script>
import Header from "@/components/Header";
import TodoList from "@/components/TodoList";
import AddTodo from "@/components/AddTodo";
export default {
  name: "App",
  components: {
    Header,
    TodoList,
    AddTodo,
  },
  data() {
    return {
      todos: [],
      filter: "all",
    };
  },
  mounted() {
    fetch("https://jsonplaceholder.typicode.com/todos?_limit=3")
      .then((response) => response.json())
      .then((json) => (this.todos = json));
  },
  computed: {
    filteredTodos() {
      if (this.filter === "all") return this.todos;

      if (this.filter === "completed")
        return this.todos.filter((todo) => todo.completed);

      if (this.filter === "not-completed")
        return this.todos.filter((todo) => !todo.completed);
      else {
        return this.todos;
      }
    },
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
    addTodo(todo) {
      this.todos = [...this.todos, todo];
    },
  },
};
</script>
