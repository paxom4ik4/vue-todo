<template>
  <div id="app">
    <Header />
    <TodoList v-bind:todos="todos" @remove-todo="removeTodo" />
  </div>
</template>

<script>
import Header from "@/components/Header";
import TodoList from "@/components/TodoList";
export default {
  name: "App",
  components: {
    Header,
    TodoList,
  },
  data() {
    return {
      todos: [
        { id: 1, title: "Learn Vue", completed: false },
        { id: 2, title: "Learn Angular", completed: false },
        { id: 3, title: "Learn React", completed: false },
      ],
    };
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
