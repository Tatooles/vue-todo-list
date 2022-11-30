<script setup lang="ts">
import { ref } from 'vue'

let id = 0

const todos = ref([
  { id: id++, text: 'example todo' }
])
</script>

<template>
  <div class="card">
    <h2>Enter your todo items below:</h2>

    <ul>
      <li v-for="todo in todos" :key="todo.id">
        {{ todo.text }}
      </li>
    </ul>
  </div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
