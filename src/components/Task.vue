<template>
  <div
    @dblclick="$emit('toggle-reminder', task.id)"
    :class="[task.reminder ? 'reminder' : '', 'flex']"
  >
    <div>
      <h3>{{ task.text }}</h3>
      <p>{{ task.day }}</p>
    </div>
    <button @click="$emit('delete-task', task.id)">x</button>
  </div>
</template>

<script>
export default {
  name: "TaskComponent",
  props: {
    task: Object,
  },
};
</script>

<style scoped>
.flex {
  display: flex;
  justify-content: space-between;
  text-align: left;
  background: rgb(227, 227, 227);
  padding: 0 10px;
  margin: 5px 10px;
  border-radius: 5px;
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