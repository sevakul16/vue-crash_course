<script setup>
import { ref } from "vue";
const name = ref("John Doe");
const status = ref("offline");
const tasks = ref(["Task 1", "Task 2", "Task 3"]);
const link = "https://www.google.com";
const newTask = ref("");

const toggleStatus = () => {
  status.value = status.value === "online" ? "offline" : "online";
};

const addTask = () => {
  if (newTask.value) {
    tasks.value.push(newTask.value);
    newTask.value = "";
  }
};

const deleteTask = (index) => {
  tasks.value.splice(index, 1);
};
</script>

<template>
  <h1>{{ name }}</h1>
  <h2 v-if="status === 'online'">User is online</h2>
  <h2 v-else-if="status === 'offline'">User is offline</h2>
  <h2 v-else>User status is unknown</h2>

  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" v-model="newTask" />
    <button type="submit" @click="addTask">Add</button>
  </form>

  <ul>
    <li v-for="(task, index) in tasks" :key="task">
      <span> {{ task }} </span>
      <button @click="deleteTask(index)">Delete</button>
    </li>
  </ul>
  <a :href="link">Google</a>
  <button @click="toggleStatus">Go online</button>
</template>
