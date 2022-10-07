<template>
  <header>
    <h1>{{ title }}</h1>
    <div class="btn-container">
      <button class="btn" @click="$emit('info-click')">info</button>
      <Button
        @btn-click="$emit('btn-click')"
        :text="taskText ? 'Close' : 'Add Task'"
        :color="taskText ? 'red' : 'green'"
      />
    </div>
  </header>
</template>

<script>
import Button from "./Button.vue";
export default {
  name: "HeadComponent",
  components: {
    Button,
  },
  props: {
    title: String,
    taskText: Boolean,
  },
  emits: ["btn-click"],
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
.btn-container {
  display: flex;
}
.btn {
  display: inline-block;
  background: none;
  color: black;
  border: 0.5px solid black;
  padding: 5px 14px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
}
button:focus {
  outline: none;
}
</style>