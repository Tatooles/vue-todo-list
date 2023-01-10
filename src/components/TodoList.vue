<script setup lang="ts">
import { ref } from 'vue'

let id = 0

const currentText = ref('')

const todos = ref([
  { id: id++, text: 'example todo' }
])

const completed = ref([
  { id: id++, text: 'example completed' }
])

const addItem = () => {
  todos.value.push({ id: id++, text: currentText.value })
  currentText.value = ''
}

const removeItem = (todo: any) => {
  todos.value = todos.value.filter(t => t !== todo)
}

const completeItem = (todo: any) => {
  todos.value = todos.value.filter(t => t !== todo)
  completed.value.push(todo)
}

const sortList = () => {
  todos.value.sort((a, b) => {
    if (a.text < b.text) {
      return -1
    } else if (a.text > b.text) {
      return 1
    } else {
      return 0
    }
  })
}

const reverseList = () => {
  todos.value.reverse()
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
      <li class="flex justify-between mt-2 hover:bg-gray-400 rounded-md pl-2 align-middle border-gray-600 border-2"
        v-for="todo in todos" :key="todo.id">
        {{ todo.text }}
        <div>
          <button class="bg-green-500 p-1 rounded-md mr-1" @click="completeItem(todo)">Done</button>
          <button class="bg-red-600 p-1 rounded-md" @click="removeItem(todo)">Delete</button>
        </div>
      </li>
    </ul>

    <button @click="sortList" class="bg-gray-500 rounded-md mt-8 mb-2">Sort list</button>
    <button @click="reverseList" class="bg-gray-500 rounded-md">Reverse Order</button>

    <div class="mt-3">
      <h2>Completed items</h2>
      <ul>
        <li v-for="item in completed" :key="item.id">
          {{ item.text }}
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped>

</style>
