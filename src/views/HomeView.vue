<template>
  <TaskForm 
    v-show= "showAddTask" 
    @add-task= "addTask" 
  />
  <TaskList 
    :tasks= "tasks" 
    @toggle-reminder = "toggleReminder"
    @delete-task = "deleteTask"
  />
</template>

<script>
import TaskList from '../components/TaskList'
import TaskForm from '../components/TaskForm'

export default {
  name: 'HomeView',
  props: {
    showAddTask: Boolean
  },
  components: {
    TaskList,
    TaskForm
  },
  data() {
    return {
      tasks: []
    }
  },
  methods: {
    addTask(task) {      
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id) {
      if(confirm('Are you sure?')) {
        this.tasks = this.tasks.filter((task) => task.id !== id )
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map( 
        (task) => task.id === id ? {...task, reminder: !task.reminder} : task)
    }
  
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Meeting at campus',
        day: 'Today at 6pm',
        reminder: false
      },
      {
        id: 2,
        text: 'Meeting at college',
        day: 'Tomorrow at 3pm',
        reminder: false
      }
    ]
  }
}
</script>
