<template>
  <div class="container">
    <h2>Добавить задачу</h2>
    <form @submit.prevent="addTask">
      <div class="mb-3">
        <label for="title" class="form-label">Заголовок:</label>
        <input v-model="newTask.title" type="text" class="form-control" id="title" required>
      </div>
      <div class="mb-3">
        <label for="description" class="form-label">Описание:</label>
        <textarea v-model="newTask.description" class="form-control" id="description" rows="3" required></textarea>
      </div>
      <button type="submit" class="btn btn-primary">Добавить</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: {
        title: "",
        description: "",
        completed: false,
      },
    };
  },
  methods: {
    addTask() {
      this.$emit("add-task", this.newTask);

      this.newTask = {
        title: "",
        description: "",
        completed: false,
      };
    },
  },
};
</script>

<style>
</style>