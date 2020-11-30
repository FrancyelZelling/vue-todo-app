<template>
  <div id="app">
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import Todos from "../components/Todos.vue";
import AddTodo from "../components/AddTodo.vue";
import axios from "axios";

interface TodoInterface {
  id: string;
  title: string;
  completed: boolean;
}

export default Vue.extend({
  name: "App",
  components: {
    Todos,
    AddTodo,
  },
  data() {
    return {
      todos: [] as TodoInterface[],
    };
  },
  methods: {
    deleteTodo(id: string) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(
          (res) => (this.todos = this.todos.filter((todo) => todo.id !== id))
        )
        .catch((err) => console.log(err));
    },
    addTodo(newTodo: TodoInterface) {
      const { title, completed } = newTodo;

      axios
        .post("https://jsonplaceholder.typicode.com/todos", {
          title,
          completed,
        })
        .then((res) => (this.todos = [...this.todos, res.data]))
        .catch((err) => console.log(err));
    },
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=10")
      .then((res) => (this.todos = res.data))
      .catch((err) => console.log(err));
  },
});
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;

  &:hover {
    background: #666;
  }
}
</style>
