<script setup lang="ts">
defineProps<{ display: string }>()
</script>

<template>
  <button>{{ display }}</button>
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
