<template>
    <div v-if='showAddTask'>
        <AddTask @add-task="addTask" />
    </div>
    <Tasks @toggle-reminder="toggleReminder" @delete-task='deleteTask' :tasks="tasks" />
</template>

<script>
import Tasks from '../components/Tasks.vue';
import AddTask from '../components/AddTask.vue';
export default {
  name: "Home",
  props : {
    showAddTask : Boolean
  } ,
  components: {
    Tasks,
    AddTask,
   
},
  data() {
    return { tasks: []}
  },
  methods: {
    async addTask(task) {
      await fetch("http://localhost:5000/tasks", {
        method: "POST",
        headers: {
          'Content-type': 'application/json',
        },
        body: JSON.stringify(task)
      })
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id) {
      if (confirm("Are you sure")) {
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => task.id === id ? { ...task, reminder: !task.reminder } : task)
    },
    async fectTasks() {
      const res = await fetch("http://localhost:5000/tasks")
      const data = await res.json()
      return data
    },
  },
  async created() {
    this.tasks = await this.fectTasks()
  },

}

</script>