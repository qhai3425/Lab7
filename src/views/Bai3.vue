<template>
    <div class="registration-container">
      <!-- Form đăng ký -->
      <div class="form-container">
        <h3>Form Đăng Ký</h3>
        <form @submit.prevent="register">
          <div class="form-group">
            <label for="fullname">Họ tên:</label>
            <input type="text" id="fullname" v-model="fullname" placeholder="Nhập họ tên">
          </div>
          <div class="form-group">
            <label for="email">Email:</label>
            <input type="email" id="email" v-model="email" placeholder="Nhập email">
          </div>
          <div class="form-group">
            <label for="password">Mật khẩu:</label>
            <input type="password" id="password" v-model="password" placeholder="Nhập mật khẩu">
          </div>
          <div class="form-group">
            <label for="birthdate">Ngày sinh:</label>
            <input type="date" id="birthdate" v-model="birthdate">
          </div>
          
          <!-- Giới tính (cập nhật dạng hàng ngang) -->
          <div class="form-group gender-group">
            <label>Giới tính:</label>
            <label for="male">
              <input type="radio" id="male" value="Nam" v-model="gender"> Nam
            </label>
            <label for="female">
              <input type="radio" id="female" value="Nữ" v-model="gender"> Nữ
            </label>
            <label for="other">
              <input type="radio" id="other" value="Khác" v-model="gender"> Khác
            </label>
          </div>
          
          <!-- Ngôn ngữ (cập nhật dạng hàng ngang) -->
          <div class="form-group language-group">
            <label>Ngôn ngữ:</label>
            <label for="vietnamese">
              <input type="checkbox" id="vietnamese" value="Tiếng Việt" v-model="languages"> Tiếng Việt
            </label>
            <label for="english">
              <input type="checkbox" id="english" value="Tiếng Anh" v-model="languages"> Tiếng Anh
            </label>
            <label for="japanese">
              <input type="checkbox" id="japanese" value="Tiếng Nhật" v-model="languages"> Tiếng Nhật
            </label>
          </div>
  
          <button type="submit">Đăng ký</button>
        </form>
      </div>
  
      <!-- Thông tin đăng ký -->
      <div class="info-container" v-if="isRegistered">
        <h3>Thông tin đã đăng ký:</h3>
        <p><strong>Họ tên:</strong> {{ fullname }}</p>
        <p><strong>Email:</strong> {{ email }}</p>
        <p><strong>Ngày sinh:</strong> {{ birthdate }}</p>
        <p><strong>Giới tính:</strong> {{ gender }}</p>
        <p><strong>Ngôn ngữ:</strong> {{ languages.join(', ') }}</p>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const fullname = ref('');
  const email = ref('');
  const password = ref('');
  const birthdate = ref('');
  const gender = ref('');
  const languages = ref([]);
  const isRegistered = ref(false);
  
  const register = () => {
    if (fullname.value && email.value && password.value && birthdate.value && gender.value && languages.value.length > 0) {
      isRegistered.value = true;
    }
  };
  </script>
  
  <style scoped>
  /* Tổng thể */
  .registration-container {
    display: flex;
    justify-content: space-between;
    gap: 30px;
    margin-top: 20px;
  }
  
  /* Form đăng ký */
  .form-container {
    flex: 1;
    max-width: 45%;
    background-color: #fff;
    padding: 15px;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    border: 1px solid #ccc;
  }
  
  h3 {
    text-align: center;
    font-size: 20px;
    margin-bottom: 15px;
    font-weight: bold;
  }
  
  .form-group {
    margin-bottom: 12px;
  }
  
  label {
    display: block;
    font-size: 14px;
    font-weight: bold;
    margin-bottom: 5px;
  }
  
  input[type="text"],
  input[type="email"],
  input[type="password"],
  input[type="date"],
  input[type="radio"],
  input[type="checkbox"] {
    width: 100%;
    padding: 10px;
    font-size: 14px;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
  }
  
  input[type="radio"],
  input[type="checkbox"] {
    width: auto;
    display: inline-block;
    margin-right: 10px;
  }
  
  /* Đặt các lựa chọn Giới tính và Ngôn ngữ nằm ngang */
  .gender-group label,
  .language-group label {
    display: inline-block;
    margin-right: 20px;
  }
  
  /* Button */
  button {
    width: 100%;
    padding: 10px;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 14px;
  }
  
  button:hover {
    background-color: #0056b3;
  }
  
  /* Kết quả đăng ký */
  .info-container {
    flex: 1;
    max-width: 45%;
    background-color: #fff;
    padding: 15px;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    border: 1px solid #ccc;
  }
  
  .info-container h3 {
    text-align: center;
    font-size: 20px;
    font-weight: bold;
    margin-bottom: 15px;
  }
  
  .info-container p {
    font-size: 14px;
    margin: 6px 0;
  }
  
  .info-container strong {
    font-weight: bold;
  }
  </style>
  