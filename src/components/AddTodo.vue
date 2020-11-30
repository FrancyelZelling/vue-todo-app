<template>
  <div>
    <form @submit="addTodo">
      <input type="text" name="title" v-model="title" placeholder="Add Todo" />
      <input type="submit" value="Submit" class="btn" />
    </form>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  name: "AddTodo",
  data() {
    return {
      title: "",
    };
  },
  methods: {
    addTodo(e: HTMLFormElement) {
      e.preventDefault();
      const newTodo = {
        title: this.title,
        completed: false,
      };
      this.$emit("add-todo", newTodo);

      this.title = "";
    },
  },
});
</script>

<style lang="scss" scoped>
form {
  display: flex;
}

input {
  &[type="text"] {
    flex: 10;
    padding: 5px;
  }

  &[type="submit"] {
    flex: 2;
  }
}
</style>
