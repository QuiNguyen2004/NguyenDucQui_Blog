---
title: "Lộ Trình Học Tập"
layout: "page"
url: "/posts"
hidemeta: true
---

<style>
/* 1. Ẩn tiêu đề và danh sách bài viết cũ bên dưới */
.page-header, .post-entry, .paginav { display: none !important; }

/* 2. Cấu hình khung chia đôi */
.post-content { margin: 0 !important; padding: 0 !important; max-width: 100% !important; width: 100% !important; }

.split-container {
display: flex;
width: 100%;
height: 80vh; /* Cao 80% màn hình */
border-radius: 25px; /* Bo tròn góc */
overflow: hidden;
box-shadow: 0 15px 40px rgba(0,0,0,0.2);
font-family: sans-serif;
margin-top: 20px;
}

.split-side {
flex: 1;
display: flex;
justify-content: center;
align-items: center;
text-decoration: none !important;
transition: all 0.5s ease;
position: relative;
overflow: hidden;
cursor: pointer;
}

/* Hiệu ứng khi di chuột: Bên nào được chọn sẽ to ra */
.split-side:hover { flex: 2; }

/* MÀU NỀN CỘT TRÁI (JAVA) */
.side-java { background: #2c3e50; color: white; }

/* MÀU NỀN CỘT PHẢI (JS) */
.side-js { background: #f1c40f; color: black; }

.split-content { text-align: center; z-index: 10; transition: transform 0.3s; }
.split-side:hover .split-content { transform: scale(1.1); }

.split-title { font-size: 3rem; font-weight: bold; display: block; text-transform: uppercase; }
.split-desc { font-size: 1.2rem; margin-top: 10px; display: block; }

/* --- CHỈNH SỬA LOGO NỀN MỜ --- */
.bg-img {
position: absolute;
top: 50%;     
left: 50%;      
transform: translate(-50%, -50%); 
width: 30%;     
opacity: 0.15;
pointer-events: none;
filter: grayscale(100%);
transition: opacity 0.5s;
}

/* Khi di chuột vào thì ảnh rõ hơn chút */
.split-side:hover .bg-img { opacity: 0.25; }

/* Mobile */
@media(max-width:768px){ .split-container{flex-direction:column; height:80vh;} .split-title{font-size:2rem;} }
</style>

<div class="split-container">
    <a href="/NguyenDucQui_Blog/posts/java-full-course/" class="split-side side-java">
        <img src="https://upload.wikimedia.org/wikipedia/en/3/30/Java_programming_language_logo.svg" class="bg-img">
        <div class="split-content">
            <span class="split-title">Java</span>
            <span class="split-desc">Tư duy Logic & Backend</span>
        </div>
    </a>
    <a href="/NguyenDucQui_Blog/posts/js-full-course/" class="split-side side-js">
        <img src="https://upload.wikimedia.org/wikipedia/commons/9/99/Unofficial_JavaScript_logo_2.svg" class="bg-img">
        <div class="split-content">
            <span class="split-title">JavaScript</span>
            <span class="split-desc">Sáng tạo Giao diện</span>
        </div>
    </a>
</div>