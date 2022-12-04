<template>
  <form @submit.prevent="submitEdits">
    <label for="edit-todo"><span class="edit">Edit: </span> {{label}}</label>
    <input type="text" id="edit-todo" v-model.trim="newLabel" ref="labelInput">
    <div class="todo-btns">

      <button @click="onSubmit">Confirm</button>
      <button @click="onCancel">Cancel</button>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      newLabel: "",
    };
  },
  props: {
    label: {
      type: String,
      required: true,
    },
    id: {
      type: Boolean,
      required: true,
    },
  },
  methods: {
    onCancel() {
      this.$emit("edit-cancled");
    },
    onSubmit() {
      this.$emit("todo-submitted", this.newLabel, this.id);
      this.newLabel = "";
    },
  },
  mounted() {
    const labelInput = this.$refs.labelInput;
    labelInput.focus();
  },
};
</script>

<style >
.edit {
  color: crimson;
  font-weight: bolder;
}
</style>