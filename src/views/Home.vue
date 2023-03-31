<template>
    <div v-if="showAddtask">
      <AddTask @add-task="addTask" />
    </div>
    <Tasks
      @toggle-reminder="toggleReminder"
      @delete-task="deleteTask"
      :tasks="tasks"
    />
    <!-- //vbind tasks to tasks data  -->
</template>

<script>
  import Tasks from "../components/Tasks";
  import AddTask from "../components/AddTask";
  export default {
    name: "Home",
    components: {
      Tasks,
      AddTask
    },
    data: {
      tasks: []
    },
    methods: {
 
    async addTask(task) {
      const res = await fetch("api/tasks", {
        method: "POST",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(task),
      });
      const data = await res.json();
      this.tasks = [...this.tasks, data];
    },
    async deleteTask(id) {
      if (confirm("Are you sure?")) {
        //request:
        const res = await fetch(`api/tasks/${id}`, {
          method: "DELETE",
        });
        res.status === 200
          ? (this.tasks = this.tasks.filter((task) => task.id !== id))
          : alert("Error deleting task");
      }
    },
    async toggleReminder(id) {
      const taskToToggle = await this.fetchTask(id);
      //get the id
      const updTask = { ...taskToToggle, reminder: !taskToToggle.reminder };
      //change the remonder in the client
      const res = await fetch(`api/tasks/${id}`, {
        method: "PUT", //request
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(updTask),
      });
      console.log("res", res);

      const data = await res.json();
      console.log("data", data);
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !data.reminder } : task
      );
    },
    async fetchTasks() {
      const res = await fetch("api/tasks");
      const data = await res.json();
      return data;
    },
    async fetchTask(id) {
      const res = await fetch(`api/tasks/${id}`);
      const data = await res.json();
      return data;
    },
  },
  async created() {
    this.tasks = await this.fetchTasks();
  },







  }
</script>