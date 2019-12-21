<template>
  <!-- bind a class (is-complete) to be applied if condition is met-->
  <!-- todo.completed = true -->
  <!-- Events to interact with todos (v-on directive) -->
  <!-- v-on:click , v-on:submit... -->
  <div class="todo-item" v-bind:class="{ 'is-complete': todo.completed }">
    <p>
      <input type="checkbox" v-on:change="markComplete" />
      {{ todo.title }}
      <!-- Important, we want to delete an item, we are traversing upward (TodoItem->Todos->App) to reach the data, we need to emmit an event -->
      <!-- use @click or v-on:click -->
      <button class="del" v-on:click="$emit('del-todo', todo.id)">x</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
};
</script>

<style scoped>
.todo-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}

.is-complete {
  text-decoration: line-through;
}

.del {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>
