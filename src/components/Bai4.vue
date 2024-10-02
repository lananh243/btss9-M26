<template>
  <div>
    <h3>Tiến độ hoàn thành : {{ progress }} %</h3>
    <input type="range" v-model="progress" />
  </div>
</template>

<script setup>
import { ref } from "vue";

const progress = ref("");
</script>

<style></style>
