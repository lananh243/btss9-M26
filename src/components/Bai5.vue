<template>
  <div>
    <h3>Giới tính : {{ gender }}</h3>
    <input type="radio" value="Nam" v-model="gender" /> Nam
    <input type="radio" value="Nữ" v-model="gender" /> Nữ
    <input type="radio" value="Khác" v-model="gender" /> Khác
  </div>
</template>

<script setup>
import { ref } from "vue";

const gender = ref("");
</script>

<style></style>
