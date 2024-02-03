<template>
      <div>
    <h2>Добавить новую задачу</h2>
    <form @submit.prevent="addTask">
      <label for="title">Заголовок:</label>
      <input v-model="newTask.title" type="text" id="title" required>
      <br><br>
      <label for="description">Описание:</label>
      <textarea v-model="newTask.description" id="description" required></textarea>
      <br><br>
      <button type="submit">Добавить</button>
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
h3 {
    margin: 0px;
}
</style>