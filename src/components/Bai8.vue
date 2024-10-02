<template>
  <form class="form" @submit.prevent="handleSubmit">
    <b class="title">Thêm mới sản phẩm</b>
    <div class="include">
      <p>Họ và tên</p>
      <input type="text" v-model="information.name" />
      <p>Email</p>
      <input type="email" v-model="information.email" />
      <p>Mật khẩu</p>
      <input type="password" v-model="information.password" />
      <p>Nhập lại mật khẩu</p>
      <input type="password" v-model="information.rePassword" />
      <br /><br />
      <button>Thêm mới</button>
    </div>
  </form>
</template>

<script setup>
import { reactive } from "vue";

const information = reactive({
  name: "",
  email: "",
  password: "",
  rePassword: "",
});

const handleSubmit = (e) => {
  console.log("Thông tin người dùng", information);
};
</script>

<style scoped>
.form {
  width: 350px;
  height: 450px;
  border: 1px solid grey;
}
.title {
  display: flex;
  justify-content: center;
  margin-top: 30px;
}
.include {
  width: 280px;
  margin: auto;
}
input {
  width: 100%;
  padding: 6px;
}
button {
  width: 295px;
  background-color: blue;
  color: white;
  border: none;
  height: 35px;
  border-radius: 5px;
}
</style>
