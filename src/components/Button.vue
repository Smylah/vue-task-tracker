<template>
  <button @click="$emit('btn-click')" :style="{ background: color }">
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "ButtonComponent",
  data() {
    return {
      count: 1,
    };
  },
  props: {
    text: String,
    color: String,
  },
};
</script>

<style scoped>
button {
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
button:focus {
  outline: none;
}
</style>