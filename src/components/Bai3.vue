<template>
  <div>
    <h3>Ngày sinh : {{ date }}</h3>
    <input type="date" v-model="date" />
  </div>
</template>

<script setup>
import { ref } from "vue";

const date = ref("");
</script>

<style></style>
