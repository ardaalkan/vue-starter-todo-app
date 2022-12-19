<template>
  <label for="todoText"></label>
  <!-- <input
    @keydown.enter="addNewTodo"
    type="text"
    id="todoText"
    class="input_handler"
    placeholder="Add Todo"
  /> -->
  <input
    v-model="todoText"
    @keydown.enter="addNewTodo(todoText)"
    type="text"
    id="todoText"
    class="input_handler"
    placeholder="Add Todo"
  />
</template>

<script>
export default {
  props: {
    addNewTodo: {
      type: Function,
      required: true,
    },
  },
  data() {
    return {
      todoText: null,
    };
  },
  methods: {
    // addNewTodo() {
    //   this.$emit("add-todo", this.todoText);
    //   this.todoText = null;
    // },
  },
};
</script>
