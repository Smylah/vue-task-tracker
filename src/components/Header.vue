<template>
  <header>
    <h1>{{ title }}</h1>
    <Button
      @btn-click="$emit('btn-click')"
      :text="taskText ? 'Close' : 'Add Task'"
      :color="taskText ? 'red' : 'green'"
    />
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
</style>