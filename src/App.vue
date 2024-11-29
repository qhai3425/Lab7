<template>
  <div id="app">
    <nav>
      <router-link to="/bai1">Bài 1</router-link>
      <router-link to="/bai2">Bài 2</router-link>
      <router-link to="/bai3">Bài 3</router-link>
      <router-link to="/bai4">Bài 4</router-link>
    </nav>

    <!-- Router View để hiển thị nội dung của các route -->
    <router-view />
  </div>
</template>

<script setup>
import { ref } from 'vue';
</script>

<style scoped>
/* Kiểu dáng cho thanh điều hướng */
nav {
  display: flex;
  justify-content: center;
  gap: 15px;
  margin-bottom: 20px;
  background-color: #f4f4f4; /* Màu nền nhạt cho điều hướng */
  padding: 10px 20px;
  border-radius: 8px; /* Bo góc nhẹ */
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); /* Hiệu ứng đổ bóng */
}

nav a {
  text-decoration: none;
  color: #555;
  font-weight: 600;
  padding: 8px 15px;
  border: 2px solid transparent;
  border-radius: 5px;
  transition: all 0.3s ease-in-out; /* Hiệu ứng chuyển đổi */
}

nav a:hover {
  background-color: #007bff; /* Màu nền khi hover */
  color: white;
}

nav a.active {
  background-color: #0056b3; /* Màu khi đang chọn */
  color: white;
  border-color: #0056b3;
}
</style>
