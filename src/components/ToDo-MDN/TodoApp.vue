<template>
  <header>

    <h1>My Todo App</h1>
  </header>
  <main class="todo-app">
    <ToDoForm @todo-added="addTodo" />
    <TodoList :todos="ToDoItems" @edit-label="editLabel" />
  </main>
</template>

<script>
import TodoList from "./TodoList.vue";
import ToDoForm from "./ToDoForm.vue";
import uniqueId from "lodash.uniqueid";

export default {
  components: {
    TodoList,
    ToDoForm,
  },
  methods: {
    addTodo(todoLabel) {
      console.log("added a todo", todoLabel);
      this.ToDoItems.push({
        id: uniqueId("todo-"),
        label: todoLabel,
        done: false,
      });
    },
    editLabel(newLabel, id) {
      const todo = this.ToDoItems.find((t) => t.id === id);
      console.log("todo => ", todo);
      if (newLabel !== "" && newLabel !== todo.label) {
        todo.label = newLabel;
      }
    },
  },
  data() {
    return {
      ToDoItems: [
        {
          id: uniqueId("todo-"),
          label: "Watch Important WC matches",
          done: false,
        },
        {
          id: uniqueId("todo-"),
          label: "play the weekly football match ",
          done: true,
        },
        { id: uniqueId("todo-"), label: "learn vue", done: false },
        { id: uniqueId("todo-"), label: "have fun", done: false },
      ],
    };
  },
};
</script>

<style>
body {
  /* background: linear-gradient(to bottom, #4b6cb7, #182848); */
  background: linear-gradient(65deg, #4b6cb7, #182848);
  color: #fff;
}
/* h1 {
  margin-bottom: 2rem;
}
.todo-app {
  box-shadow: 2px 2px 15px rgb(186, 186, 186);
  min-height: 30vh;
  width: 80vw;
  margin-inline: auto;
  padding: 1rem;
  font-size: 1.25rem;
  border-radius: 1.5rem;
}

ToDoForm {
  border: 2px solid green;
} */
</style>
