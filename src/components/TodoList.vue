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
  <div class="flex flex-col text-center">
    <h2 class="text-lg font-bold my-2">Enter your todo items below:</h2>
    <form @submit.prevent="addItem">
      <input class="border-2 rounded-md border-black mr-2" v-model="currentText">
      <button class="rounded-lg bg-green-400 p-3">Add Item</button>
    </form>

    <ul>
      <li v-for="todo in todos" :key="todo.id">
        {{ todo.text }}
        <button class="bg-red-600 p-1 rounded-md" @click="removeItem(todo)">X</button>
      </li>
    </ul>
  </div>
</template>

<style scoped>

</style>
