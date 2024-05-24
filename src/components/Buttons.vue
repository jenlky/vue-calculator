<script setup lang="ts">
defineProps<{
  val: string
}>()
</script>

<template>
  <button>{{ val }}</button>
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
}

button:last-of-type {
  background-color: #FFFFFF;
  color: black;
}
</style>
