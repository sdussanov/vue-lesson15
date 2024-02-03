<template>
    <div>
        <h3>Задачи:</h3>
        <div class="task" v-for="(task, index) in tasks" :key="index">
            <Task :task="task" />
            Номер: {{ task.id }}<br>
            Статус: {{ task.completed }}<br>
        </div>
        <p>Всего задач в пуле: {{ totalTasks }}</p>
        <TaskForm @add-task="addTask" />
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
        }
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
    }
}
</script>

<style>
.task {
    width: 30%;
    border: 1px solid black;
    border-radius: 10px;
    padding: 10px;
    margin-bottom: 10px;
}
</style>