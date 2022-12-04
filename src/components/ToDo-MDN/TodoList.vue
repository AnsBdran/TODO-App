<template>
  <h2>{{todosSummary}}</h2>
  <ul class="todos">
    <li class="todo" v-for="todo in todos" :key="todo.id">
      <TodoItem :label="todo.label" :done="todo.done" :id="todo.id" @checkbox-changed="updateCheck(todo.id)" @emittedEdit="handleEdit" @edit-label="editLabel" />
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
    // handleEdit() {
    //   this.isEditing = true;
    // },
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
</style>
