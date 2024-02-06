<template>
    <div class="container">
        <div class="text-center">
            <h2>Список задач</h2>
        </div>

        <div v-for="(task, index) in tasks" :key="index">
            <Task :task="task" @delete-task="deleteTask" @toggle-completed="toggleCompleted" />
        </div>
        <TaskForm @add-task="addTask" />
        <p>Всего задач: {{ tasks.length }}</p>
        <p>Выполнено задач: {{ completedTasks }}</p>
    </div>
</template>

<script>
import Task from '../components/Task.vue'
import TaskForm from '../components/TaskForm.vue'

export default {
    props: ['tasks'],
    computed: {
        totalTasks() {
            return this.tasks.length
        },
        completedTasks() {
            return this.tasks.filter(task => task.completed).length;
        },
    },
    components: {
        Task,
        TaskForm
    },
    methods: {
        addTask(newTask) {
            this.tasks.push({
                id: this.tasks.length + 1,
                title: newTask.title,
                description: newTask.description,
                completed: false,
            });
        },
        deleteTask(taskId) {
            console.log('Удаляю в TaskList')
            this.$emit("delete-task", taskId);
        }
    }
}
</script>

<style></style>