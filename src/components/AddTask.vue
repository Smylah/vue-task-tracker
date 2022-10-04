<template>
  <form @submit="onSubmit">
    <div>
      <label>Task</label>
      <input type="text" name="text" placeholder="Add Task" v-model="text" />
    </div>
    <div>
      <label>Day & Time</label>
      <input
        type="text"
        name="day"
        placeholder="Add Day and Time"
        v-model="day"
      />
    </div>
    <div class="checkbox">
      <label>Set Reminder</label>
      <input type="checkbox" name="reminder" v-model="reminder" />
    </div>
    <!-- <Button text="Submit" color="black" /> -->
    <button type="submit" value="Save Task" class="btn">Save Task</button>
  </form>
</template>

<script>
// import Button from "./Button.vue";

export default {
  name: "AddTask",
  components: {
    // Button,
  },
  data() {
    return {
      text: "",
      day: "",
      reminder: false,
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      if (!this.text) {
        alert("please add a task");
        return;
      }
      const newTask = {
        id: Math.floor(Math.random() * 10000),
        text: this.text,
        day: this.day,
        reminder: this.reminder,
      };
      this.$emit("add-task", newTask);

      this.text = "";
      this.day = "";
      this.reminder = false;
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin: 0 10px;
}
div {
  text-align: left;
}
input {
  box-sizing: border-box;
  width: 100%;
}
.checkbox {
  display: flex;
}
.btn {
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
.btn:focus {
  outline: none;
}
</style>