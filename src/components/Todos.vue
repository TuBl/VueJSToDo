<template>
  <!-- v-for to loop, first todo is whatever name, second matches props -->
  <div>
    <div v-bind:key="todo.id" v-for="todo in todos">
      <!-- we got our todo from looping over our todos, we then pass it as a prop to TodoItem -->
      <!-- we wanna catch the emit event from our todoItem via  v-on:(nameOfEmittedEvent), in this case v-on:del-todo -->
      <TodoItem
        v-bind:todo="todo"
        v-on:del-todo="$emit('del-todo', todo.id)"
      ></TodoItem>
    </div>
  </div>
</template>

<script>
import TodoItem from "./TodoItem";
export default {
  name: "Todos",
  components: {
    TodoItem
  },
  props: ["todos"]
};
</script>

<style scoped></style>
