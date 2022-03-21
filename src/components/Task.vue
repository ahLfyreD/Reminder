<template>
<!-- The ? sysmbol means true or false and the : sysmbol means else. take note -->
    <div @dblclick="$emit('toggle-reminder', task.id)" 
    :class="[task.reminder ? 'reminder' : '', 'task']"
    >
        <h3>
            {{ task.text }}
            <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
            <!-- another way of doing the emit on the i element without using the "method
            using this @click='$emit('delete-task', task.id)' -->
        </h3>
        <p>{{ task.day }}</p>

    </div>
    
    
</template>

<script>
export default {
    name: 'Task',
    props: {
        task: Object
    },
    // methods: {
    //     onDelete(id) {
    //         this.$emit('delete-task', id)
    //         // this is actually emiting upwards into the App.vue

    //     }
    // }

}
</script>

<style scoped>
    .fas{
        color: red;
    }
    .task {
        background: #f4f4f4;
        margin: 5px;
        padding: 10px 20px;
        cursor: pointer;
        border-radius: 5px;
        border: 1px solid black;

    }
    .task.reminder{
        border-left: 5px solid green;
    }

    .task h3{
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
</style>