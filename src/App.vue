<script setup>
import { ref } from "vue";
const name = ref("John Doe");
const status = ref("offline");
const tasks = ref([
  { id: 1, title: "Task 1" },
  { id: 2, title: "Task 2" },
  { id: 3, title: "Task 3" },
]);
const link = "https://www.google.com";

const toggleStatus = () => {
  status.value = status.value === "online" ? "offline" : "online";
};
</script>

<template>
  <h1>{{ name }}</h1>
  <h2 v-if="status === 'online'">User is online</h2>
  <h2 v-else-if="status === 'offline'">User is offline</h2>
  <h2 v-else>User status is unknown</h2>
  <ul>
    <li v-for="task in tasks" :key="task.id">
      {{ task.title }}
    </li>
  </ul>
  <a :href="link">Google</a>
  <button @click="toggleStatus">Go online</button>
</template>
