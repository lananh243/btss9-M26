<template>
  <form class="form" @submit.prevent="handleSubmit">
    <h3 class="title">Đăng Ký Tài Khoản</h3>
    <div class="include">
      <p>Họ và tên</p>
      <input type="text" v-model="information.name" ref="nameInput" />
      <div v-if="errInput.name" class="error">{{ errInput.name }}</div>

      <p>Email</p>
      <input type="email" v-model="information.email" />
      <div v-if="errInput.email" class="error">{{ errInput.email }}</div>

      <p>Mật khẩu</p>
      <input type="password" v-model="information.password" />
      <div v-if="errInput.password" class="error">{{ errInput.password }}</div>

      <p>Số điện thoại</p>
      <input type="text" v-model="information.phone" />
      <div v-if="errInput.phone" class="error">{{ errInput.phone }}</div>

      <br /><br />
      <button type="submit">Đăng ký</button>
    </div>

    <div v-if="successMessage" class="success">{{ successMessage }}</div>
  </form>
</template>

<script setup>
import { reactive, ref } from "vue";

const information = reactive({
  name: "",
  email: "",
  password: "",
  phone: "",
});

const errInput = reactive({
  name: "",
  email: "",
  password: "",
  phone: "",
});

const successMessage = ref("");

// Hàm validate email định dạng cơ bản
const validateEmail = (email) => {
  const re = /\S+@\S+\.\S+/;
  return re.test(email);
};

// Hàm kiểm tra email có bị trùng không
const isEmailDuplicate = (email) => {
  const users = JSON.parse(localStorage.getItem("users") || "[]");
  return users.some((user) => user.email === email);
};

// Hàm handle submit form
const handleSubmit = () => {
  let hasError = false;

  // Reset lại thông báo lỗi
  errInput.name = "";
  errInput.email = "";
  errInput.password = "";
  errInput.phone = "";

  // Validate tên
  if (!information.name) {
    errInput.name = "Vui lòng nhập họ và tên";
    hasError = true;
  }

  // Validate email
  if (!information.email) {
    errInput.email = "Vui lòng nhập email";
    hasError = true;
  } else if (!validateEmail(information.email)) {
    errInput.email = "Email không hợp lệ";
    hasError = true;
  } else if (isEmailDuplicate(information.email)) {
    alert("Email đã tồn tại");
    hasError = true;
  }

  // Validate mật khẩu
  if (!information.password) {
    errInput.password = "Vui lòng nhập mật khẩu";
    hasError = true;
  }

  // Validate số điện thoại
  if (!information.phone) {
    errInput.phone = "Vui lòng nhập số điện thoại";
    hasError = true;
  }

  // Nếu không có lỗi, tiến hành lưu vào localStorage
  if (!hasError) {
    // Lưu thông tin người dùng vào localStorage
    const users = JSON.parse(localStorage.getItem("users") || "[]");
    users.push({ ...information });
    localStorage.setItem("users", JSON.stringify(users));

    // Hiển thị thông báo thành công
    alert("Đăng ký tài khoản thành công!");

    // Xóa các giá trị input
    information.name = "";
    information.email = "";
    information.password = "";
    information.phone = "";

    // Focus lại vào ô input Tên sinh viên nếu tồn tại
    if (nameInput.value) {
      nameInput.value.focus();
    }
  }
};

// Tham chiếu tới ô input Tên sinh viên
const nameInput = ref(null);
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
  margin-top: 20px;
}
.include {
  width: 100%;
  margin: auto;
}
input {
  width: 330px;
  padding: 6px;
  margin-bottom: 10px;
}
button {
  width: 100%;
  background-color: blue;
  color: white;
  border: none;
  height: 35px;
  border-radius: 5px;
}
.error {
  color: red;
}
.success {
  color: green;
  text-align: center;
  margin-top: 10px;
}
</style>
