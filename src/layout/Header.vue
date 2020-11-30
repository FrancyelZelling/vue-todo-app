<template>
  <header class="header">
    <h1>TodoList</h1>
    <div id="nav">
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
    </div>
  </header>
</template>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  name: "Header",
});
</script>

<style lang="scss" scoped>
.header {
  background: #333;
  color: #fff;
  text-align: center;
  padding: 10px;

  a {
    color: #fff;
    font-size: 0.9rem;
    padding-right: 5px;
    text-decoration: none;
    margin: 10px;
    border: 2px solid #fff;
    border-radius: 10px;
    padding: 2px 6px;
  }
}
</style>
