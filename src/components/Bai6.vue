<template>
  <div>
    <h3>Sở thích : {{ hobbies }}</h3>
    <input type="checkbox" v-model="hobbies" value="Đá bóng" /> Đá bóng
    <input type="checkbox" v-model="hobbies" value="Bóng chuyền" /> Bóng chuyền
    <input type="checkbox" v-model="hobbies" value="Code" /> Code
    <input type="checkbox" v-model="hobbies" value="Bơi lội" /> Bơi lội
  </div>
</template>

<script setup>
import { ref } from "vue";

const hobbies = ref([]);
</script>

<style></style>
