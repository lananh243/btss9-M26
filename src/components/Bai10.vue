<template>
  <form class="form" @submit.prevent="handleSubmitForm">
    <h3 class="title">Đăng nhập tài khoản</h3>
    <div class="include">
      <p>Email</p>
      <input type="email" v-model="information.email" />
      <p v-if="error.email" class="error">{{ error.email }}</p>
      <p>Mật khẩu</p>
      <input type="password" v-model="information.password" />
      <p v-if="error.password" class="error">{{ error.password }}</p>
      <br /><br />
      <button type="submit">Đăng nhập</button>
    </div>
  </form>
</template>

<script setup>
import { reactive } from "vue";

const information = reactive({
  email: "",
  password: "",
});

const error = reactive({
  email: "",
  password: "",
});

const handleSubmitForm = () => {
  let hasError = false;

  error.email = "";
  error.password = "";

  if (!information.email) {
    error.email = "Vui lòng nhập email";
    hasError = true;
  }

  if (!information.password) {
    error.password = "Vui lòng nhập mật khẩu";
    hasError = true;
  }

  if (hasError) return;

  const users = JSON.parse(localStorage.getItem("users") || "[]");

  const user = users.find(
    (account) =>
      account.email === information.email &&
      account.password === information.password
  );

  if (user) {
    alert("Đăng nhập thành công");
  } else {
    alert("Đăng nhập thất bại");
  }
};
</script>

<style scoped>
.form {
  width: 350px;
  height: auto;
  border: 1px solid grey;
  padding: 20px;
}
.title {
  display: flex;
  justify-content: center;
  margin-top: 30px;
}
.include {
  width: 330px;
}
input {
  width: 100%;
  padding: 6px;
}
button {
  width: 340px;
  background-color: blue;
  color: white;
  border: none;
  height: 35px;
  border-radius: 5px;
}
.error {
  color: red;
}
</style>
