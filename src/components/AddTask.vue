<template>
  <div>
 <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Task</label>
      <!-- v-model allows to bind data from the form -->
      <input type="text" v-model="text" name="text" placeholder="Add Task" />
    </div>
    <div class="form-control">
      <label>Day &amp; Time</label>
        <!-- v-model allows to bind data from the form -->
      <input
        type="text"
        v-model="day"
        name="day"
        placeholder="Add Day &amp; Time"
      />
    </div>
    <div class="form-control form-control-check">
      <label>Set Reminder</label>
        <!-- v-model allows to bind data from the form -->
      <input type="checkbox" v-model="reminder" name="reminder" />
    </div>

    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>
  </div>
</template>

<script>
export default {
  name: 'AddTask',
  data() {
    return {
      text: "",
      day: "",
      reminder: false
    }
  },
  methods: {
    onSubmit(e) {
      e.preventDefault()
      if (!this.text) {
        alert("Please eneter a task")
        return
      }
      const newTask = {
        id: Math.floor(Math.random() * 100000),
        text: this.text,
        day: this.day,
        reminder: this.reminder
      }
      this.text = "",
      this.day = "",
      this.remonder = false
    }
  }
}


</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>

