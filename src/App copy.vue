<script>
export default {
  data() {
    return {
      message: "Welcome to Your Vue.js App",
      status: `active`,
      tasks: ["task1", "task2", "task3"],
      link: "https://google.com",
    };
  },
  methods: {
    toggleStatus() {
      this.status = this.status === "active" ? "pending" : "inactive";
    },
  },
};
</script>
<template>
  <h1>{{ message }}</h1>
  <p v-if="status === `active`">user is active</p>
  <p v-else-if="status === `pending`">user is pending</p>
  <p v-else>user is inactive</p>

  <h2>tasks</h2>

  <ul>
    <li v-for="item in tasks" :key="item">{{ item }}</li>
  </ul>
  <!-- <a v-bind:href="link">click for google</a> -->
  <a :href="link">click for google</a>
  <button @:click="toggleStatus">change status</button>
</template>

<style scoped></style>
