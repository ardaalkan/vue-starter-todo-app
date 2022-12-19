<template>
  <li class="todo_li">
    <span>{{ item.text }} #</span>
    <button @click="deleteItem(item)" class="btn">Sil</button>
  </li>
</template>
<script>
export default {
  props: ["item"],
  inject: ["deleteItem"],
};
</script>
