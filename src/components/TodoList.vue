<template>
  <div
    class="card p-3"
    :class="{ 'visually-hidden': todos.length == 0 ? true : false }">
    <ul class="list-unstyled mb-0">
      <TodoItem
        v-for="(todo, index) in todos"
        :key="index"
        :todo="todo"
        @delete-todo="deleteTodoHandler(index)"
        @completed-toggle="completedToggleHandler(index)" />
    </ul>
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";

export default {
  name: "TodoList",
  components: {
    TodoItem
  },
  data() {
    return {};
  },
  props: {
    todos: Array
  },
  methods: {
    deleteTodoHandler(index) {
      this.$emit("delete-todo", index);
    },
    completedToggleHandler(index) {
      this.$emit("completed-toggle", index);
    }
  }
};
</script>

<style scoped></style>
