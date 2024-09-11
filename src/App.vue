<script setup>
import { ref } from "vue";

const name = ref("jon doe");
const status = ref("active");
const tasks = ref(["task1", "task2", "task3"]);
const newTask = ref("");

const toggleStatus = () => {
  if (status.value === "active") {
    status.value = "pending";
  } else if (status.value === "pending") {
    status.value = "inactive";
  } else {
    status.value = "active";
  }
};
function addTask() {
  if (newTask.value.trim() !== "") {
    tasks.value.push(newTask.value);
    newTask.value = "";
  }
  console.log(`clicked`);
}
function deleteTask(index) {
  // tasks.value.splice(index, 1);
  tasks.value.splice(index, 1);
}
</script>
<template>
  <h1>{{ name }}</h1>
  <p v-if="status === `active`">user is active</p>
  <p v-else-if="status === `pending`">user is pending</p>
  <p v-else>user is inactive</p>

  <form action="" @submit.prevent="addTask">
    <label for="new task">Add Task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask" />
    <button type="submit">submit</button>
  </form>
  <h2>tasks</h2>
  <ul>
    <li v-for="(item, index) in tasks" :key="item">
      <span>{{ item }}</span>
      <button @click="deleteTask(index)">x</button>
    </li>
  </ul>
  <button @:click="toggleStatus">change status</button>
</template>
