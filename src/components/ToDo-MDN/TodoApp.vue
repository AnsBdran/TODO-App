<template>
  <header>
    <h1 class="highlight">My Todo App</h1>
  </header>
  <main class="todo-app">
    <ToDoForm @todo-added="addTodo" />
    <TodoList :todos="ToDoItems" @edit-label="editLabel" @delete-todo="deleteTodo" />
  </main>
  <footer>
    <p>Made with <img src="../../assets/imgs/heart.svg" alt="heart img"> By: Anas Badran</p>
  </footer>
</template>

<script>
import TodoList from "./TodoList.vue";
import ToDoForm from "./ToDoForm.vue";
import uniqueId from "lodash.uniqueid";
// import TodoItemVue from "./TodoItem.vue";

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
    deleteTodo(id) {
      const idx = this.ToDoItems.findIndex((t) => t.id === id);
      this.ToDoItems.splice(idx, 1);
      console.log("idx", idx);
    },
  },
  data() {
    return {
      ToDoItems: [
        {
          id: uniqueId("todo-"),
          label: "Eat",
          done: false,
        },
        {
          id: uniqueId("todo-"),
          label: "Drink",
          done: true,
        },
        { id: uniqueId("todo-"), label: "Code", done: false },
        { id: uniqueId("todo-"), label: "Sleep", done: false },
        { id: uniqueId("todo-"), label: "Repeat", done: false },
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
  min-height: 100vh;
}

h1,
h2 {
  width: max-content;
  margin-inline: auto;
}
h1 {
  color: #c8cede;
}
h1.highlight::before {
  top: 3rem;
}

.todo-app {
  border: 4px solid #051537;
  margin-top: 2rem;
}

footer p {
  color: #1f1f4d;
}
footer img {
  width: 1.2em;
  vertical-align: middle;
  margin-bottom: 0.2em;
  /* max-height: 100%; */
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
