<template>
<div class="container">
  <Header title='Task Tracker' />
  <Tasks @toggle-reminder='toggleReminder' @delete-task='deleteTask' :tasks= 'tasks' />
</div>  
</template>

<script>

import Header from './components/Header'
import Tasks from './components/Tasks'

export default {
  name: 'App',
  components: {
    Header,
    Tasks,  
  },
  data () {
    return {
      tasks: []
    }
  },
  methods: {
    deleteTask(id) {
      if(confirm('Are you sure?')){
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
      
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => task.id === id
      ? {...task, reminder: !task.reminder} : task )
      // Map is recommended to toggle the reminder since we are updating the task by changing the reminder from either true to false
      // or false to true. Map allows us to basically manipulate the array and return
      // the array of whatever we want and here, we want a return of updated tasks
    // => means forEach
    },

  },
  created() {
    this.tasks = [

      {
        id: 1,
        text: 'Meeting at School',
        day: 'March 3rd at 1:30pm',
        reminder: true,
      },
      {
        id: 2,
        text: 'Play Football',
        day: 'March 3rd at 4:30pm',
        reminder: true,
      },
      {
        id: 3,
        text: 'Go for your HIV test',
        day: 'March 4th at 8:00am',
        reminder: false,
      }
    ]
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins&display=swap');

*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body{
  font-family: 'Poppins', sans-serif;
}

.container{
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 10px 20px;
  border-radius: 5px;
}
.btn{
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn-focus{
  outline: none;
}
.btn:active{
  transform: scale(0.98);
}
.btn-block{
  display: block;
  width: 100%;
}
</style>
