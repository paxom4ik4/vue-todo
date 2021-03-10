<template>
  <form @submit.prevent="onSubmit">
    <input
      type="text"
      name=""
      id=""
      v-model="title"
      placeholder="What To Do?"
    />
    <button type="submit">Create</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: "",
    };
  },
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          completed: false,
        };
        this.$emit("add-todo", newTodo);
        this.title = "";
      }
    },
  },
};
</script>

<style scoped>
form {
  width: 100%;
  height: 50px;
  justify-content: center;
  align-items: center;
  display: flex;
}
input {
  padding: 0 5px;
  height: 50%;
  width: 50%;
}
button {
  height: 50%;
  margin: 0 20px;
  padding: 0 10px;
}
</style>