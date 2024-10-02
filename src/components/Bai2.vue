<template>
  <div>
    <h3>Màu sắc</h3>
    <input type="color" v-model="color" />
    <h4>Mã màu : {{ color }}</h4>
  </div>
</template>

<script setup>
import { ref } from "vue";

const color = ref("");
</script>

<style></style>
