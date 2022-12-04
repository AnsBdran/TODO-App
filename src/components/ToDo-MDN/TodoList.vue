<template>
  <h2 class="highlight">{{todosSummary}}</h2>
  <ul class="todos">
    <li class="todo" v-for="todo in todos" :key="todo.id">
      <TodoItem :label="todo.label" :done="todo.done" :id="todo.id" @checkbox-changed="updateCheck(todo.id)" @emittedEdit="handleEdit" @edit-label="editLabel" @delete-todo="deleteTodo" />
      <!-- <ToDoEditForm v-else /> -->
    </li>
  </ul>
</template>

<script>
import TodoItem from "./TodoItem.vue";
// import ToDoEditForm from "./ToDoEditForm.vue";

export default {
  components: {
    TodoItem,
    // ToDoEditForm,
  },
  data() {
    return {
      // isEditing: false,
    };
  },
  props: ["todos"],
  methods: {
    updateCheck(id) {
      const todoToUpdate = this.todos.find((t) => t.id === id);
      console.log(todoToUpdate);
      todoToUpdate.done = !todoToUpdate.done;
      // return todoToUpdate.done;
    },
    editLabel(newLabel, id) {
      this.$emit("edit-label", newLabel, id);
    },
    deleteTodo(id) {
      console.log(id, "deleted");
      this.$emit("delete-todo", id);
    },
  },
  computed: {
    todosSummary() {
      const doneTodos = this.todos.filter((t) => t.done).length;
      return `${doneTodos} out of ${this.todos.length} items completed`;
    },
  },
};
</script>

<style>
.todo {
  margin: 2rem;
}
.highlight {
  position: relative;
  /* border: 0.6px solid red; */

  height: auto;
  padding: 0 0.2em;
  /* border-radius: 8px; */
}

.highlight::before {
  content: "";
  position: absolute;
  background-color: #0a295ee2;
  left: 0;
  right: 0;
  bottom: 0;
  top: 3.5rem;
  z-index: -1;
  transition: 0.2s;
}

.highlight:hover::before {
  top: 0;
  /* bottom: 0; */
  /* height: auto; */
}
</style>
