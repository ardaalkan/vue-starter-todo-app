<template>
  <ul class="todo_ul">
    <!-- <li v-for="todo in todoList" :key="todo" class="todo_li">
      <span>Todo Item #{{ todo.id }}</span>
      <button @click="deleteItem(todo)" class="btn">Sil</button>
    </li> -->
    <TodoListItem
      @delete-todo-item="$emit('delete-todo-item', $event)"
      v-for="todoItem in provideData.todoList"
      :key="todoItem.id"
      :item="todoItem"
    />
  </ul>
</template>

<script>
import TodoListItem from "@/components/TodoListItem.vue";
export default {
  // props: ["myData"],
  inject: ["provideData"],
  // props : {
  //   myData: {
  //     type: String,
  //     required: false,
  //     default: "",
  //   }
  // },
  components: {
    TodoListItem,
  },
};
</script>
