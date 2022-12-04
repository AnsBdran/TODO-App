<template>
  <form @submit.prevent="onSubmit">
    <label for="new-todo">
      <h2>What needs to be done?</h2>
    </label>
    <input type="text" id="new-todo" name="new-todo" autocomplete="off" v-model.trim="label">
    <button>Add</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      label: "",
    };
  },
  methods: {
    onSubmit() {
      //   e.preventDefault()
      //   console.log('form submitted')
      //   console.log(this.label)

      this.label && this.$emit("todo-added", this.label);
      this.label = "";
    },
  },
};
</script>

<style >
form {
  /* width: max-content; */
  width: 80%;
  margin: 5rem auto;
  /* border: 2px solid gray; */
}
input {
  display: block;
  margin: 1.6rem auto 0.8rem;
  outline: none;
  padding: 0.4em;
  /* font: inherit; */
  border-radius: 8px;
  width: 100%;
}
button {
  /* padding: 0.4em; */
  /* min-width: 5rem; */
  /* font: inherit; */
  border-radius: 8px;
  min-width: 8rem;
  width: 100%;
}

h2 {
  text-align: center;
}
</style>
