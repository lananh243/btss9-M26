<template>
  <form @submit.prevent="handleSubmit">
    <h2>User Name : {{ userInfo.userName }}</h2>
    <h2>DateOfBirth : {{ userInfo.dateOfBirth }}</h2>
    <h2>Gender : {{ userInfo.gender }}</h2>
    <h2>Hobbies : {{ userInfo.hobbies }}</h2>
    <h3>Thêm mới người dùng</h3>
    <div>
      Họ và tên :
      <input type="text" v-model="userInfo.userName" placeholder="Nhập tên" />
    </div>
    <div>Ngày sinh : <input type="date" v-model="userInfo.dateOfBirth" /></div>
    <div>Giới tính :</div>
    <div>
      Nam <input type="radio" v-model="userInfo.gender" value="0" /> Nữ
      <input type="radio" v-model="userInfo.gender" value="1" /> Khác
      <input type="radio" v-model="userInfo.gender" value="2" />
    </div>
    <div>Sở thích</div>
    <div>
      <input type="checkbox" v-model="userInfo.hobbies" value="game" /> Chơi
      game
      <input type="checkbox" v-model="userInfo.hobbies" value="code" /> Code
      <input type="checkbox" v-model="userInfo.hobbies" value="swim" /> Bơi lội
      <input
        type="checkbox"
        v-model="userInfo.hobbies"
        value="volleyball"
      />Bóng chuyền
      <input type="checkbox" v-model="userInfo.hobbies" value="soccer" />Bóng đá
    </div>
    <button>Thêm</button>
  </form>
</template>

<script setup>
import { reactive, ref } from "vue";

// const userName = ref("");

// const dateOfBirth = ref("");

// const gender = ref("0");

// const hobbies = ref([]);

const userInfo = reactive({
  userName: "",
  dateOfBirth: "",
  gender: "0",
  hobbies: [],
});

const handleSubmit = (event) => {
  // Ngăn chặn sự kiện load lại trang
  //   event.preventDefault();

  console.log("Submit", userInfo);

  //   const user = {
  //     userName: userName.value,
  //     dateOfBirth: dateOfBirth.value,
  //     gender: gender.value,
  //     hobbies: hobbies.value,
  //   };
};
</script>

<style></style>
