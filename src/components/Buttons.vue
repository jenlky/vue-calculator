<script setup lang="ts">
defineProps<{ value:string }>()

// function clickHandler(e) {
//   console.log(e.currentTarget.textContent)
// }
</script>

<template>
  <button @click="$emit('clickHandler', e)">{{ value }}</button>
</template>

<style scoped>
button {
  background-color: #37474F;
  color: #FFFFFF;
  width: 50px;
  margin: 2px;
  font-size: 18px;
  font-family: sans-serif;
  line-height: inherit;
  border: 0;
  cursor: pointer;
}

button:last-of-type {
  background-color: #FFFFFF;
  color: black;
}
</style>
