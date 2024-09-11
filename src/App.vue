<script setup>
import { ref } from "vue";

const name = ref("jon doe");
const status = ref("active");
const tasks = ref(["task1", "task2", "task3"]);

const toggleStatus = () => {
  if (status.value === "active") {
    status.value = "pending";
  } else if (status.value === "pending") {
    status.value = "inactive";
  } else {
    status.value = "active";
  }
};
</script>
<template>
  <h1>{{ name }}</h1>
  <p v-if="status === `active`">user is active</p>
  <p v-else-if="status === `pending`">user is pending</p>
  <p v-else>user is inactive</p>

  <h2>tasks</h2>

  <ul>
    <li v-for="item in tasks" :key="item">{{ item }}</li>
  </ul>
  <button @:click="toggleStatus">change status</button>
</template>
