<template>
    <div :class="{ 'completed-task': task.completed }">
        <h3>Задача: {{ task.title }}</h3>
        <p>Описание: {{ task.description.substring(0, 15) }}...</p>
        <label for="completed">Выполнено</label>
        <input type="checkbox" v-model="task.completed" @change="toggleCompleted">
        <br>
        <button @click="deleteTask">Удалить</button>
        <button @click="showDetails">Подробнее</button>
        <div v-if="showDetailsBox" class="details-box">
            <slot name="details">
            </slot>
            <button @click="hideDetails">Закрыть</button>
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
h3 {
    margin: 0px;
}

h4 {
    margin: 0px;
}

.details-box {
    border: 1px solid black;
    padding: 10px;
    margin-top: 10px;
}

.completed-task {
  background-color: aquamarine;
}
</style>