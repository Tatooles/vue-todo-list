<script setup lang="ts">
import { ref } from 'vue'

let id = 0

const currentText = ref('')

const todos = ref([
  { id: id++, text: 'example todo' }
])

const addItem = () => {
  todos.value.push({ id: id++, text: currentText.value })
  currentText.value = ''
}

const removeItem = (todo: any) => {
  todos.value = todos.value.filter(t => t !== todo)
}
</script>

<template>
  <div class="card">
    <h2 class="underline">Enter your todo items below:</h2>
    <form @submit.prevent="addItem">
      <input v-model="currentText">
      <button>Add Item</button>
    </form>

    <ul>
      <li v-for="todo in todos" :key="todo.id">
        {{ todo.text }}
        <button @click="removeItem(todo)">X</button>
      </li>
    </ul>
  </div>
</template>

<style scoped>

</style>
