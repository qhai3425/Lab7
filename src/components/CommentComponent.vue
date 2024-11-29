<template>
  <div class="col-sm-4 m-5">
    <h2>Bình luận bài viết</h2>
    <div class="card">
      <img src="../assets/images/image.png" alt="Hình ảnh" />
      <div class="card-body">
        <h3 class="card-title">8 loại rau củ quả giàu canxi</h3>
        <p class="card-text">
          Canxi là khoáng chất cần thiết đối với cơ thể người. Có nhiều cách để
          biir sung canxi, trung đó bổ sung qua đường ăn uống là cách tốt nhất.
          Có 8 loại rau củ quả giàu canxi...
        </p>
      </div>
    </div>
    <form @submit.prevent="submitComment">
      <div class="mt-3">
        <textarea
          id="commentText"
          cols="60"
          v-model="commentText"
          placeholder="Nhập bình luận"
        ></textarea>
      </div>
      <button class="btn btn-success">Gửi bình luận</button>
    </form>

    <div v-if="comments.length" class="mt-3">
      <h5>Danh sách các bình luận:</h5>
      <ul style="list-style-type: circle">
        <li v-for="(comment, index) in comments" :key="index">
          <p>
            <strong>{{ comment.name }}</strong
            >: {{ comment.text }}
          </p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const props = defineProps(["username"]);

const commentText = ref("");

const comments = ref([]);

function submitComment() {
  if (commentText.value) {
    comments.value.push({
      name: props.username,
      text: commentText.value,
    });

    commentText.value = "";
  }
}
</script>

<style scoped>
/* Container chính cho phần bình luận */
.col-sm-4 {
  margin: 30px auto; /* Căn giữa và thêm khoảng cách */
  padding: 20px;
  background-color: #fff;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); /* Tạo độ sâu */
}

/* Tiêu đề phần bình luận */
h2 {
  text-align: center;
  color: #333;
  font-size: 24px;
  margin-bottom: 20px;
}

/* Card chứa bài viết */
.card {
  margin-bottom: 20px;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

.card img {
  width: 100%;
  height: auto;
  border-bottom: 1px solid #ddd;
}

.card-body {
  padding: 15px;
}

.card-title {
  font-size: 20px;
  color: #007bff; /* Màu xanh dương cho tiêu đề */
  font-weight: bold;
}

.card-text {
  color: #555;
  font-size: 14px;
  line-height: 1.6;
}

/* Form nhập bình luận */
textarea {
  width: 100%;
  padding: 12px;
  font-size: 14px;
  border-radius: 8px;
  border: 1px solid #ccc;
  box-sizing: border-box;
  resize: vertical;
  min-height: 100px;
  margin-bottom: 15px;
  transition: border-color 0.3s ease;
}

textarea:focus {
  border-color: #007bff;
  outline: none;
}

/* Nút gửi bình luận */
button {
  width: 100%;
  padding: 12px;
  font-size: 16px;
  color: white;
  background-color: #28a745; /* Màu xanh lá cây */
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #218838; /* Màu đậm hơn khi hover */
}

/* Danh sách bình luận */
h5 {
  font-size: 18px;
  color: #333;
  margin-bottom: 10px;
}

ul {
  list-style-type: circle;
  padding-left: 20px;
}

li {
  margin-bottom: 10px;
}

li p {
  font-size: 14px;
  color: #555;
}

strong {
  color: #007bff; /* Màu xanh cho tên người dùng */
}
</style>
