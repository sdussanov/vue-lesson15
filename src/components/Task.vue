<template>
    <div class="card">
        <div :class="{ 'completed-task': task.completed }">
            <div class="card-body">
                <h5 class="card-title">{{ task.title }}</h5>
                <p class="card-text">{{ task.description.substring(0, 15) }}...</p>
                <div class="form-check form-switch">
                    <input class="form-check-input" type="checkbox" v-model="task.completed" @change="toggleCompleted">
                    <label class="form-check-label" for="completed">Выполнено</label>
                </div>
                <div class="text-center">
                    <button class="btn btn-danger" @click="deleteTask">Удалить</button>
                    <button class="btn btn-primary" @click="showDetails">Подробнее</button>
                </div>
                <div v-if="showDetailsBox" class="details-box">
                    <h5>Подробнее о {{ task.title }}</h5>
                    <p>{{ task.description }}</p>
                    <div class="text-center">
                        <button class="btn btn-secondary" @click="hideDetails">Закрыть</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            showDetailsBox: false
        }
    },
    props: ['task'],
    methods: {
        deleteTask() {
            //console.log('Удаляю в Task')
            this.$emit("delete-task", this.task.id);
        },
        toggleCompleted() {
            this.$emit("toggle-completed", this.task.id);
        },
        showDetails() {
            console.log('Открыл подробнее')
            this.showDetailsBox = true;
        },
        hideDetails() {
            console.log('Скрыл подробнее')
            this.showDetailsBox = false;
        }
    }
}

</script>

<style>
.completed-task {
    background-color: lightgreen;
    color: blue;
}
</style>