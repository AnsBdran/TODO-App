<template>
  <ToDo />
</template>

<script>
import ToDo from "./components/ToDo-MDN/TodoApp.vue";

export default {
  name: "App",
  components: {
    ToDo,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  /* color: #2c3e50; */
  /* margin-top: 60px; */
}

/* *:active {
  filter: drop-shadow(2px 2px 10px rgba(51, 51, 51, 0.048));
} */
</style>
