<template>
  <div class="input-group mb-3">
    <input class="form-control" type="text" v-model="title" />
    <select class="form-select flex-grow-0 w-auto py-3" v-model="importance">
      <option value="normal">一般</option>
      <option value="important">重要</option>
      <option value="urgent">緊急</option>
    </select>
    <button class="btn btn-primary py-3" @click="addTodo">新增</button>
  </div>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      title: "",
      importance: "normal"
    };
  },
  methods: {
    addTodo() {
      this.$emit("add-todo", {
        title: this.title,
        importance: this.importance
      });
      this.title = "";
      this.importance = "normal";
    }
  }
};
</script>

<style scoped></style>
