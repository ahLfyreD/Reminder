
<template>
    <div :key='task.id' v-for='task in tasks'>
        <Task @toggle-reminder="$emit('toggle-reminder', task.id)" @delete-task="$emit('delete-task', task.id)" :task='task' />
    </div>
    <!-- v-for is used to create a list or we can loop through and output something -->
    
</template>

<script>
// dont forget to always register as a component in the export dafault
import Task from './Task'

export default {
    name: 'Tasks',
    props: {
        tasks: Array
    },
    components: {
        Task
    },
    emits: ['delete-task', 'toggle-reminder'],
}
</script>

<style scoped>
    
</style>