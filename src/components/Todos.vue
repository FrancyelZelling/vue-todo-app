<template>
  <div class="">
    <div v-bind:key="todo.id" v-for="todo in todos">
      <TodoItem v-bind:todo="todo" />
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import TodoItem from "./TodoItem.vue";

export default Vue.extend({
  name: "Todos",
  components: {
    TodoItem,
  },
  props: ["todos"],
});
</script>

<style lang="scss" scoped>
</style>
