<template>
  <div>
    <AddTodo @add-todo="addTodo" />
    <div class="select-container">
      <select v-model="filter">
        <option value="all">All</option>
        <option value="completed">Completed</option>
        <option value="not-completed">Not Completed</option>
      </select>
    </div>
    <div class="todos-container">
      <TodoList
        v-bind:todos="filteredTodos"
        @remove-todo="removeTodo"
        v-if="filteredTodos.length"
      />
      <p v-else>No Todos</p>
    </div>
  </div>
</template>

<script>
import TodoList from "@/components/TodoList";
import AddTodo from "@/components/AddTodo";
export default {
  name: "App",
  components: {
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
<style scoped>
.select-container {
  width: 100%;
  display: flex;
  justify-content: flex-start;
  align-items: center;
}
select {
  display: flex;

  margin: 10px 0 20px 30px;
}
</style>