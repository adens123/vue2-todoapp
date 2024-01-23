<template>
  <div>
    <AddTodo @add-todo="addTodoHandler" />
    <TodoList
      :todos="todos"
      @delete-todo="deleteTodoHandler"
      @completed-toggle="completedToggleHandler" />
  </div>
</template>

<script>
import AddTodo from "./components/AddTodo.vue";
import TodoList from "./components/TodoList.vue";

export default {
  name: "App",
  components: {
    TodoList,
    AddTodo
  },
  data() {
    return {
      todos: []
    };
  },
  methods: {
    addTodoHandler(todo) {
      this.todos.push({ ...todo, completed: false });
    },
    deleteTodoHandler(index) {
      this.todos.splice(index, 1);
    },
    completedToggleHandler(index) {
      this.todos[index].completed = !this.todos[index].completed;
    }
  },
  watch: {
    todos: {
      handler() {
        localStorage.setItem("todos", JSON.stringify(this.todos));
      },
      deep: true
    }
  },
  mounted() {
    if (localStorage.getItem("todos")) {
      this.todos = JSON.parse(localStorage.getItem("todos"));
    }
  }
};
</script>

<style></style>
