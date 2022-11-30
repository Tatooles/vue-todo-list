<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import HelloWorld from './components/HelloWorld.vue'
import { ref } from 'vue';
import TodoList from './components/TodoList.vue';

const showHome = ref(true)

const hideHome = () => {
  showHome.value = false;
}
</script>

<template>
  <button v-if="showHome" @click="hideHome">Hide Home Screen</button>
  <HelloWorld v-if="showHome" msg="Vite + Vue" msg2="second message" />
  <TodoList v-if="!showHome" />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
