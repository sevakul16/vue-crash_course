<script>
export default {
  name: "App",
  data() {
    return {
      name: "Seva",
      tasks: [
        { id: 1, title: "Task 1", done: false },
        { id: 2, title: "Task 2", done: true },
        { id: 3, title: "Task 3", done: false },
      ],
      status: "offline",
      link: "https://www.google.com",
    };
  },
  methods: {
    toggleStatus() {
      this.status = this.status === "online" ? "offline" : "online";
    },
  },
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
