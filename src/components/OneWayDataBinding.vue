<template>
  <div>
    <h1>One Way Databinding</h1>
    <h3>UserName : {{ userName }}</h3>

    <input type="text" name="" id="" :value="userName" />

    <button @click="handleChangeName">Change Name</button>
  </div>
</template>

<script setup>
import { ref } from "vue";

const userName = ref("Lan Anh");

const handleChangeName = () => {
  userName.value = "Nguyễn Lan Anh";
};
</script>

<style></style>
