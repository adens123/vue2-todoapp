<template>
  <li class="form-control d-flex align-items-center border-secondary mb-3">
    <span
      :style="{ color: color }"
      :class="{ 'text-decoration-line-through': todo.completed ? true : false }"
      >{{ todo.title }}</span
    ><span
      :style="{
        display: todo.completed ? 'inline-block' : 'none'
      }"
      >(已完成)</span
    ><button class="btn btn-success ms-auto" @click="completedToggle">
      標示為已完成</button
    ><button class="btn btn-danger ms-1" @click="deleteTodo">刪除</button>
  </li>
</template>

<script>
export default {
  name: "TodoItem",
  props: {
    todo: Object
  },
  data() {
    return {};
  },
  computed: {
    color() {
      if (this.todo.importance == "important") {
        return "orange";
      }
      if (this.todo.importance == "urgent") {
        return "red";
      }
      return "";
    }
  },
  methods: {
    deleteTodo() {
      this.$emit("delete-todo");
    },
    completedToggle() {
      this.$emit("completed-toggle");
    }
  }
};
</script>

<style scoped></style>
