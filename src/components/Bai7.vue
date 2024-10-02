<template>
  <form class="form" @submit.prevent="handleSubmit">
    <b class="title">Thêm mới sản phẩm</b>
    <div class="include">
      <p>Mã sản phẩm</p>
      <input type="text" v-model="product.codeProduct" />
      <p>Tên sản phẩm</p>
      <input type="text" v-model="product.name" />
      <p>Giá</p>
      <input type="text" v-model="product.price" />
      <p>Số lượng</p>
      <input type="number" v-model="product.quantity" />
      <br /><br />
      <button>Thêm mới</button>
    </div>
  </form>
</template>

<script setup>
import { reactive } from "vue";

const product = reactive({
  codeProduct: "",
  name: "",
  price: "",
  quantity: 0,
});

const handleSubmit = (e) => {
  console.log("Sản phẩm", product);
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
}
</style>
