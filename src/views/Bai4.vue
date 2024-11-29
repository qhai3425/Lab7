<template>
  <div class="bai4-container">
    <!-- Hiển thị form đăng nhập hoặc giao diện bình luận -->
    <div v-if="!isLoggedIn">
      <LoginComponent @loggedIn="handleLoginSuccess" />
    </div>
    <div v-else>
      <CommentComponent :username="loggedInUser" />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import LoginComponent from '../components/LoginComponent.vue';
import CommentComponent from '../components/CommentComponent.vue';

const isLoggedIn = ref(false); // Trạng thái đăng nhập
const loggedInUser = ref('');  // Tên người dùng đã đăng nhập

// Xử lý đăng nhập thành công
function handleLoginSuccess(username) {
  loggedInUser.value = username;
  isLoggedIn.value = true;
}
</script>

<style scoped>
/* Container chính */
.bai4-container {
  padding: 30px;
  max-width: 600px; /* Giới hạn chiều rộng nhỏ hơn để gọn hơn */
  margin: 50px auto; /* Căn giữa và thêm khoảng cách trên */
  background-color: #ffffff; /* Màu nền trắng tinh tế */
  border-radius: 10px; /* Bo góc lớn hơn */
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15); /* Đổ bóng rõ nét hơn */
  font-family: 'Roboto', sans-serif; /* Font chữ hiện đại */
  color: #333; /* Màu chữ trung tính */
}

/* Khu vực đăng nhập */
.login-section {
  margin-bottom: 20px;
  text-align: center;
}

/* Khu vực bình luận */
.comment-section {
  margin-bottom: 20px;
}

/* Tiêu đề chính */
h2 {
  text-align: center;
  margin-bottom: 20px;
  font-size: 24px;
  color: #222; /* Màu đậm hơn cho tiêu đề */
}

/* Nút bấm */
button {
  display: inline-block;
  width: 100%; /* Kéo dài nút full width */
  padding: 12px;
  font-size: 16px;
  font-weight: bold;
  color: #ffffff;
  background-color: #007bff; /* Xanh chủ đạo */
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.2s ease;
}

button:hover {
  background-color: #0056b3; /* Xanh đậm hơn */
  transform: scale(1.02); /* Hiệu ứng zoom nhẹ khi hover */
}

button:active {
  background-color: #003f7f; /* Xanh đậm hơn nữa khi nhấn */
  transform: scale(0.98); /* Hiệu ứng thu nhỏ khi click */
}

/* Input chung */
input {
  width: 100%;
  padding: 12px;
  margin-bottom: 15px; /* Khoảng cách giữa các input */
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 8px;
  box-sizing: border-box;
  transition: border-color 0.3s ease;
}

input:focus {
  outline: none;
  border-color: #007bff; /* Màu xanh khi focus */
}

/* Phần thông báo lỗi */
.error {
  color: #ff4d4f; /* Màu đỏ nổi bật */
  font-size: 14px;
  margin-top: -10px;
  margin-bottom: 10px;
}

/* Footer hoặc thông báo */
footer {
  text-align: center;
  font-size: 14px;
  color: #777;
  margin-top: 30px;
}
</style>
