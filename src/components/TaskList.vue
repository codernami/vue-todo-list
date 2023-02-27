<template>
    <div v-for= "task in tasks" :key= "task.id">
        <!-- <h3> {{ task.text }}</h3> -->
        <TaskListItem 
        :task= "task" 
        @delete-task= "$emit('delete-task', task.id)"
        @toggle-reminder= "$emit('toggle-reminder', task.id)"
        />
    </div>    
</template>

<script>
import TaskListItem from './TaskListItem'

export default {
    name: 'TaskList',
    props: {
        tasks: Array
    },
    components: {
        TaskListItem
    },
    emits: ['delete-task', 'toggle-reminder']
}
</script>