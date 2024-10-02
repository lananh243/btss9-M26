<template>
  <div>
    <h3>Email</h3>
    <input type="email" placeholder="Nhập email" v-model="email" />

    <h4>Giá trị : {{ email }}</h4>
  </div>
</template>

<script setup>
import { ref } from "vue";

const email = ref("");
</script>

<style></style>
