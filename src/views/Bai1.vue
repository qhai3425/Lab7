<template>
  <div class="task-manager col-sm-4 p-5">
    <h3 class="text-center">Quản lý công việc</h3>

    <!-- Form thêm công việc -->
    <form @submit.prevent="addList">
      <div class="mb-3">
        <label class="form-label">Tên công việc</label>
        <input
          type="text"
          class="form-control"
          v-model="newToDo"
          placeholder="Nhập tên công việc"
        />
      </div>
      <button type="submit" class="btn btn-primary">Thêm công việc</button>
    </form>

    <!-- Danh sách công việc -->
    <ul class="list-group mt-4">
      <li
        class="list-group-item d-flex justify-content-between align-items-center"
        v-for="(job, index) in jobs"
        :key="index"
      >
        {{ job }}
        <button
          class="btn btn-danger btn-sm"
          @click="removeList(index)"
        >
          Xóa
        </button>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref } from 'vue';

// Biến trạng thái
const newToDo = ref(''); // Lưu giá trị của mục cần thêm
const jobs = ref(['Ăn sáng', 'Đi học', 'Chơi bóng rổ']); // Danh sách công việc

// Hàm thêm công việc
const addList = () => {
  const task = newToDo.value.trim(); // Loại bỏ khoảng trắng thừa
  if (task) {
    jobs.value.push(task); // Thêm công việc vào danh sách
    newToDo.value = ''; // Reset ô nhập liệu
  } else {
    alert("Vui lòng nhập tên công việc!"); // Nếu không có công việc, thông báo lỗi
  }
};

// Hàm xóa công việc
const removeList = (index) => {
  jobs.value.splice(index, 1); // Xóa công việc theo chỉ mục
};
</script>

<style scoped>
/* Căn giữa phần chính */
body {
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background-color: #f5f5f5;
  font-family: Arial, sans-serif;
  font-size: 14px; /* Giảm kích thước font tổng thể */
}

/* Phần bao bọc chính */
.task-manager {
  border: 1px solid #ddd;
  border-radius: 8px;
  background-color: #ffffff;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.1);
  padding: 15px;
  max-width: 300px; /* Giảm chiều rộng tối đa */
  width: 100%;
}

/* Tiêu đề */
h3 {
  font-weight: bold;
  color: #333;
  text-align: center;
  margin-bottom: 15px;
  font-size: 1.2rem; /* Giảm kích thước font */
}

/* Form thêm công việc */
.form-label {
  font-weight: bold;
  color: #555;
  display: block;
  margin-bottom: 5px;
}

.form-control {
  border: 1px solid #ddd;
  border-radius: 5px;
  padding: 7px;
  width: 285px;
  font-size: 15px; /* Giảm kích thước font */
}

.form-control:focus {
  outline: none;
  border-color: #007bff;
  box-shadow: 0 0 4px rgba(0, 123, 255, 0.5);
}

/* Nút thêm công việc */
.btn-primary {
  background-color: #007bff;
  border: none;
  border-radius: 5px;
  color: #fff;
  padding: 10px ; /* Giảm padding */
  font-size: 0.9rem; /* Giảm kích thước font */
  width: 50%;
}

.btn-primary:hover {
  background-color: #0056b3;
}

/* Danh sách công việc */
.list-group {
  margin-top: 15px;
  padding: 0;
  list-style: none;
}

.list-group-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border: 1px solid #ddd;
  border-radius: 5px;
  margin-bottom: 8px; /* Giảm khoảng cách giữa các item */
  padding: 8px 12px; /* Giảm padding */
  background-color: #f9f9f9;
  font-size: 0.9rem; /* Giảm kích thước font */
}

.list-group-item:last-child {
  margin-bottom: 0;
}

/* Nút xóa công việc */
.btn-danger {
  background-color: #dc3545;
  border: none;
  color: #fff;
  font-size: 0.8rem; /* Giảm kích thước font */
  padding: 4px 8px; /* Giảm padding */
  border-radius: 5px;
  font-weight: bold;
  cursor: pointer;
}

.btn-danger:hover {
  background-color: #b02a37;
}
</style>
