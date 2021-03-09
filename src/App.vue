<template>
  <div id="app">
    <Header />
    <TodoList v-bind="todos" />
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
  todos: [
    { id: 1, title: "Learn Vue", completed: false },
    { id: 2, title: "Learn Angular", completed: false },
    { id: 3, title: "Learn React", completed: true }
  ]
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
