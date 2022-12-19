<template>
  <div class="todo_view">
    <h1 class="todo_welcome_text">Todos</h1>
    <AddSection :addNewTodo="addNewTodo" @add-todo="addNewTodo" />
    <ListSection />
  </div>
</template>

<script>
import AddSection from "../components/AddSection.vue";
import ListSection from "../components/ListSection.vue";

export default {
  components: {
    AddSection,
    ListSection,
  },
  created() {
    // setTimeout(() => {
    //   this.todoList = [
    //     { id: 1, text: "Bootcamp #2.0" },
    //     { id: 2, text: "Bootcamp #2.1" },
    //     { id: 3, text: "Bootcamp #2.2" },
    //     { id: 4, text: "Bootcamp #2.3" },
    //     { id: 5, text: "Bootcamp #2.4" },
    //     { id: 6, text: "Bootcamp #2.5" },
    //   ];
    // }, 2000);
  },
  data() {
    return {
      provideData: {
        todoList: [
          { id: 1, text: "Bootcamp #2.0" },
          { id: 2, text: "Bootcamp #2.1" },
          { id: 3, text: "Bootcamp #2.2" },
          { id: 4, text: "Bootcamp #2.3" },
          { id: 5, text: "Bootcamp #2.4" },
          { id: 6, text: "Bootcamp #2.5" },
        ],
      },
    };
  },
  provide() {
    return {
      provideData: this.provideData,
      deleteItem: this.deleteItem,
    };
  },
  methods: {
    deleteItem(todo) {
      console.log(this.todoList);
      // const matchedIndex = this.todoList.findIndex((i) => i === todo);
      // if (matchedIndex > -1) {
      //   this.todoList.splice(this.todoList[matchedIndex], 1);
      // }
      this.provideData.todoList = this.provideData.todoList.filter((t) => t !== todo);
    },
    addNewTodo(todo) {
      this.provideData.todoList.push({
        id: new Date().getTime(),
        text: todo,
      });
    },
  },
};
</script>

<style>
@media (min-width: 1024px) {
  .todo_view {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
  .todo_welcome_text {
    margin-bottom: 15px;
  }
  .input_handler {
    width: 100%;
    color: rgb(160, 160, 160);
    font-size: 16px;
    line-height: 20px;
    min-height: 28px;
    border-radius: 4px;
    padding: 8px 16px;
    border: 1px solid rgb(124, 124, 124);
    box-shadow: rgba(255, 255, 255, 0.12) 0px 1px 3px, rgba(117, 117, 117, 0.24) 0px 1px 2px;
    background: transparent;
    transition: all 0.1s ease 0s;
    outline: 0.5px solid rgb(71, 71, 71);
  }
  .btn {
    background-color: #4caf50; /* Green */
    border: none;
    color: white;
    padding: 19px 25px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 14px;
    cursor: pointer;
  }
  .btn:active {
    background: #3f9642;
  }
  .todo_ul {
    flex-direction: column;
    width: 100%;
    padding: 0;
  }
  /* .todo_view small {
  } */
  .todo_li {
    background-color: #303030;
    display: flex;
    align-items: center;
    width: 100%;
    justify-content: space-between;
    margin-top: 10px;
  }
  .todo_li span {
    margin-left: 15px;
  }
}
</style>
