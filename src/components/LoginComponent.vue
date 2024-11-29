<template>
  <div class="m-5 col-sm-3">
    <h2>Đăng nhập</h2>
    <form @submit.prevent="handleLogin">
      <div class="mb-3">
        <label for="username">Tên đăng nhập: </label>
        <input
          type="text"
          class="form-control"
          id="username"
          v-model="username"
          placeholder="Nhập tên đăng nhập"
        />
      </div>
      <div class="mb-3">
        <label for="password">Mật khẩu: </label>
        <input
          type="password"
          class="form-control"
          id="password"
          v-model="password"
          placeholder="Nhập mật khẩu"
        />
      </div>

      <button class="btn btn-primary" type="submit">Đăng nhập</button>
    </form>
  </div>
</template>

<script setup>
import { ref } from "vue";

const username = ref("");
const password = ref("");

const emit = defineEmits(["loggedIn"]);

function handleLogin() {
  if (username.value && password.value) {
    emit("loggedIn", username.value);
  }
}
</script>
<style scoped>
/* Container cho form đăng nhập */
.col-sm-3 {
  margin: 50px auto;
  padding: 20px;
  background-color: #fff;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

/* Tiêu đề phần đăng nhập */
h2 {
  text-align: center;
  color: #333;
  font-size: 24px;
  margin-bottom: 20px;
}

/* Các phần tử nhập liệu */
.mb-3 {
  margin-bottom: 20px;
}

label {
  display: block;
  font-size: 14px;
  color: #333;
  margin-bottom: 5px;
}

input.form-control {
  width: 100%;
  padding: 12px;
  font-size: 16px;
  border-radius: 8px;
  border: 1px solid #ccc;
  box-sizing: border-box;
  transition: border-color 0.3s ease;
}

input.form-control:focus {
  border-color: #007bff;
  outline: none;
}

/* Nút đăng nhập */
button {
  width: 100%;
  padding: 12px;
  font-size: 16px;
  color: white;
  background-color: #007bff; /* Màu xanh chủ đạo */
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #0056b3; /* Màu xanh đậm hơn khi hover */
}
</style>
