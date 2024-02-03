<template>
  <div>
    <h1>Lesson 15</h1>
    <TaskList :tasks="tasks" />
  </div>
</template> 

<script>
import TaskList from '../components/TaskList.vue'

export default {
  data() {
    return {
      tasks: [
        {
          id: 1,
          title: 'Создать проект',
          description: 'Создать проект на vue.js',
          completed: true
        },
        {
          id: 2,
          title: 'Исправить баг',
          description: 'Исправить баг со списками',
          completed: true
        },
        {
          id: 3,
          title: 'Изменить страницу',
          description: 'Изменить главную страницу сайта',
          completed: false
        }
      ]
    }
  },
  components: {
    TaskList
  }
}
</script>