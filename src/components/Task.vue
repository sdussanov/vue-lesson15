<template>
    <div>
        <h3>{{ task.title }}</h3>
        {{ task.description }}
    </div>
</template>

<script>
export default {
    props: ['task']
}
</script>

<style>
h3 {
    margin: 0px;
}
</style>