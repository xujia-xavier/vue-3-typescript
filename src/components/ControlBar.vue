<script setup lang="ts">
const emit = defineEmits<{
  (event: "add-count", num: number): void
  (event: "reset-count"): void
}>();
</script>
<template>
  <button @click="emit('add-count',1)">Add</button>
  <button @click="emit('reset-count')">Reset</button>
  <button></button>
</template>