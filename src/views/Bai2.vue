<template>
    <div v-if="!isLoggedIn" class="login-form">
      <h3>Form Đăng nhập</h3>
      <form @submit.prevent="login">
        <div class="form-group">
          <label>Email:</label>
          <input type="email" v-model="email" placeholder="Nhập email" />
          <p v-if="emailError" class="error">{{ emailError }}</p>
        </div>
        <div class="form-group">
          <label>Mật khẩu:</label>
          <input type="password" v-model="password" placeholder="Nhập mật khẩu" />
          <p v-if="passwordError" class="error">{{ passwordError }}</p>
        </div>
        <button type="submit" class="btn-primary">Đăng nhập</button>
      </form>
    </div>
  
    <div v-else class="welcome-screen">
      <h3>Chào mừng, {{ email }}!</h3>
      <button @click="logout" class="btn-primary">Đăng xuất</button>
    </div>
  </template>
  
  <script setup>
  import { ref } from "vue";
  
  const isLoggedIn = ref(false);
  const email = ref("");
  const password = ref("");
  
  const emailError = ref("");
  const passwordError = ref("");
  
  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  
  const login = () => {
    emailError.value = "";
    passwordError.value = "";
  
    if (!email.value) {
      emailError.value = "Email là bắt buộc.";
    } else if (!emailRegex.test(email.value)) {
      emailError.value = "Vui lòng nhập email hợp lệ.";
    }
  
    if (!password.value) {
      passwordError.value = "Mật khẩu là bắt buộc.";
    }
  
    if (!emailError.value && !passwordError.value) {
      isLoggedIn.value = true;
    }
  };
  
  const logout = () => {
    isLoggedIn.value = false;
    email.value = "";
    password.value = "";
    emailError.value = "";
    passwordError.value = "";
  };
  </script>
  
  <style scoped>
  /* Tổng thể */
  .login-form,
  .welcome-screen {
    max-width: 400px;
    margin: 0 auto;
    border: 1px solid #ddd;
    border-radius: 8px;
    padding: 20px;
    background-color: #fff;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  }
  
  /* Tiêu đề */
  h3 {
    text-align: center;
    margin-bottom: 20px;
    font-weight: bold;
  }
  
  /* Form input */
  .form-group {
    margin-bottom: 15px;
  }
  
  label {
    display: block;
    font-weight: bold;
    margin-bottom: 5px;
  }
  
  input {
    width: 100%;
    padding: 10px;
    font-size: 14px;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
  }
  
  input:focus {
    outline: none;
    border-color: #007bff;
  }
  
  /* Nút bấm */
  .btn-primary {
    width: 100%;
    padding: 10px;
    font-size: 16px;
    color: #fff;
    background-color: #007bff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .btn-primary:hover {
    background-color: #0056b3;
  }
  
  /* Lỗi */
  .error {
    color: red;
    font-size: 14px;
    margin-top: 5px;
  }
  </style>
  