<template>
  <li class="todo-item">
    <span v-bind:class="{ done: todo.completed }">
      <input
        type="checkbox"
        name=""
        id=""
        v-on:change="todo.completed = !todo.completed"
      />
      <strong>{{ todo.id }}</strong>
      {{ todo.title }}
    </span>
    <button class="rm" v-on:click="$emit('remove-todo', todo.id)">
      &times;
    </button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped>
li {
  border: 1px solid #ccc;
  display: flex;
  justify-content: space-between;
  padding: 0.5rem 2rem;
  margin-bottom: 1rem;
}

input {
  margin-right: 1rem;
}

.rm {
  width: 20px;
  height: 100%;
  background-color: red;
  color: #fff;
  border-radius: 50%;
  font-weight: bold;
}

.done {
  text-decoration: line-through;
}
</style>