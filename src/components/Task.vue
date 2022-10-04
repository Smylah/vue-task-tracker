<template>
  <div
    @dblclick="$emit('toggle-reminder', task.id)"
    :class="[task.reminder ? 'reminder' : '', 'flex']"
  >
    <div class="task">
      <h3>{{ task.text }}</h3>
      <p>{{ task.day }}</p>
    </div>
    <button @click="$emit('delete-task', task.id)">x</button>
  </div>
</template>

<script>
export default {
  name: "TaskComp",
  props: {
    task: Object,
  },
};
</script>

<style scoped>
div {
  display: flex;
  flex-direction: row;
  text-align: left;
  background: rgb(213, 211, 211);
  padding: 2px 3px;
  margin: 5px;
  border-radius: 5px;
}
.flex {
  display: flex;
  justify-content: space-between;
}
.task {
  display: flex;
  flex-direction: column;
}
.reminder {
  border-left: 5px solid green;
}
button {
  color: red;
  background: none;
  border: none;
  font-size: 36px;
}
</style>