<template>
  <div>
 <form class="add-form">
    <div class="form-control">
      <label>Task</label>
      <input type="text" v-model="text" name="text" placeholder="Add Task" />
    </div>
    <div class="form-control">
      <label>Day &amp; Time</label>
      <input
        type="text"
        v-model="day"
        name="day"
        placeholder="Add Day &amp; Time"
      />
    </div>
    <div class="form-control form-control-check">
      <label>Set Reminder</label>
      <input type="checkbox" v-model="reminder" name="reminder" />
    </div>

    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>
  </div>
</template>

<script>
export default {
  name: 'AddTask'
}
</script>
