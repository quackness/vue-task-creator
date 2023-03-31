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
    }
  }
</script>