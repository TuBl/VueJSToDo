<template>
  <div>
    <!-- the reason for not using $emit is because we need to construct (create a new toDo object via addToDo method)  the todo before we send it-->
    <form @submit="addTodo">
      <!-- v-model to put input -->
      <input
        type="text"
        v-model="title"
        name="title"
        placeholder="Add Todo..."
      />
      <input type="submit" value="Submit" class="btn" />
    </form>
  </div>
</template>

<script>
// import uuid from "uuid"; no longer needed, jsonplaceholder gives random id
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      const newTodo = {
        // id: uuid.v4(), no longer needed, jsonplaceholder
        title: this.title,
        completed: false
      };
      // Send up to parent
      this.$emit("add-todo", newTodo);
      // Clear field
      this.title = "";
    }
  }
};
</script>

<style scoped>
form {
  display: flex;
}

input[type="text"] {
  flex: 10;
  padding: 5px;
}

input[type="submit"] {
  flex: 2;
}
</style>
