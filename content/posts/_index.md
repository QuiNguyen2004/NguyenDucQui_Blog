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
height: 50vh; /* Cao 80% màn hình */
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
width: 20%;     
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
<style>
/* --- 1. CẤU HÌNH CONTAINER TỔNG --- */
.recent-section {
    margin-top: 60px;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    padding-bottom: 50px;
}

.section-title {
    font-size: 2rem;
    font-weight: 800; /* Siêu đậm */
    margin-bottom: 30px;
    border-left: 6px solid #2c3e50;
    padding-left: 20px;
    color: #2c3e50;
    letter-spacing: -0.5px;
}

/* Grid Layout */
.post-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(320px, 1fr)); /* Card rộng hơn xíu */
    gap: 30px;
}

/* --- 2. THIẾT KẾ CARD (ĐẸP HƠN) --- */
.post-card {
    background: #ffffff;
    border: none; /* Bỏ viền cứng */
    border-radius: 16px; /* Bo tròn mềm mại hơn */
    padding: 25px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    
    /* Đổ bóng mặc định (tạo chiều sâu) */
    box-shadow: 0 4px 20px rgba(0,0,0,0.05); 
    transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275); /* Hiệu ứng nảy */
    position: relative;
    overflow: hidden;
}

/* Hiệu ứng khi di chuột vào Card */
.post-card:hover {
    transform: translateY(-10px); /* Bay lên cao hơn */
    box-shadow: 0 15px 30px rgba(0,0,0,0.15); /* Bóng đậm hơn */
}

/* Tag/Category */
.card-tag {
    font-size: 0.75rem;
    font-weight: 800; /* Chữ tag đậm */
    text-transform: uppercase;
    letter-spacing: 1px;
    color: #2c3e50;
    background: #f0f2f5;
    padding: 6px 14px;
    border-radius: 30px;
    width: fit-content;
    margin-bottom: 15px;
}

/* Tiêu đề bài viết */
.card-title {
    font-size: 1.4rem; /* To hơn */
    font-weight: 800; /* Đậm hơn */
    margin: 10px 0 15px 0;
    color: black; 
    line-height: 1.3;
}

/* Mô tả ngắn */
.card-desc {
    font-size: 1rem;
    color: #4a5568; /* Màu xám đậm, dễ đọc hơn #666 */
    font-weight: 500; /* Tăng độ dày chữ một chút */
    margin-bottom: 25px;
    line-height: 1.6; /* Giãn dòng cho thoáng */
    display: -webkit-box;
    -webkit-line-clamp: 3;
    -webkit-box-orient: vertical;
    overflow: hidden;
}

/* Nút Đọc tiếp */
.read-more {
    text-decoration: none;
    color: #2980b9;
    font-weight: 700; /* Chữ đậm */
    font-size: 1rem;
    display: flex;
    align-items: center;
    transition: color 0.3s;
}

.read-more::after {
    content: "→";
    margin-left: 8px;
    transition: transform 0.3s;
}

.post-card:hover .read-more {
    color: #e67e22; /* Đổi màu cam khi hover card */
}

.post-card:hover .read-more::after {
    transform: translateX(5px); /* Mũi tên chạy sang phải */
}

/* --- 3. DARK MODE (GIAO DIỆN TỐI) --- */
@media (prefers-color-scheme: dark) {
    body { background-color: #121212; }
    .section-title { color: #ecf0f1; border-color: #e67e22; }
    
    .post-card { 
        background: #1e1e1e; 
        box-shadow: 0 4px 20px rgba(0,0,0,0.3);
    }
    
    .card-title { color: #ffffff; }
    .card-desc { color: #bdc3c7; font-weight: 400; } /* Chữ sáng hơn trên nền tối */
    .card-tag { background: #333; color: #ecf0f1; }
    .read-more { color: #64b5f6; }
}
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
<div class="recent-section">
    <h2 class="section-title">Bài Viết Mới Nhất</h2>   
    <div class="post-grid">
        <div class="post-card">
            <span class="card-tag">Java Core</span>
            <h3 class="card-title">Làm chủ Java Collections: ArrayList, HashSet và HashMap</h3>
            <p class="card-desc">Hướng dẫn chi tiết cách sử dụng các cấu trúc dữ liệu quan trọng nhất trong Java. Khi nào nên dùng List, khi nào dùng Map?</p>
            <a href="/NguyenDucQui_Blog/posts/javacollectionsframework/" class="read-more">Đọc tiếp</a>
        </div>
        <div class="post-card">
            <span class="card-tag">Java 8</span>
            <h3 class="card-title">Java Streams API: Tạm biệt vòng lặp for</h3>
            <p class="card-desc">Chuyển đổi tư duy từ lập trình mệnh lệnh sang khai báo. Học cách filter, map và collect dữ liệu cực ngầu.</p>
            <a href="/NguyenDucQui_Blog/posts/java8streamsapi/" class="read-more">Đọc tiếp</a>
        </div>
        <div class="post-card">
            <span class="card-tag">Tips & Tricks</span>
            <h3 class="card-title">Xử lý chuỗi (String) và tối ưu hiệu năng</h3>
            <p class="card-desc">5 hàm xử lý chuỗi bất ly thân và tại sao bạn nên dùng StringBuilder thay vì cộng chuỗi thông thường.</p>
            <a href="/NguyenDucQui_Blog/posts/javastringmethods/" class="read-more">Đọc tiếp</a>
        </div>
        <div class="post-card">
            <span class="card-tag">Best Practice</span>
            <h3 class="card-title">Xử lý lỗi chuyên nghiệp với Try-Catch</h3>
            <p class="card-desc">Cách bắt lỗi (Exception), sử dụng Multi-catch trong Java 7+ và phân biệt throw vs throws.</p>
            <a href="/NguyenDucQui_Blog/posts/exceptionhandling/" class="read-more">Đọc tiếp</a>
        </div>
        <div class="post-card">
            <span class="card-tag">Java NIO</span>
            <h3 class="card-title">Đọc ghi file hiện đại với Java NIO</h3>
            <p class="card-desc">Quên FileReader cũ kỹ đi. Khám phá cách đọc file nhanh chóng chỉ với một dòng code bằng Files.readAllLines.</p>
            <a href="/NguyenDucQui_Blog/posts/javaioandfilehandling/" class="read-more">Đọc tiếp</a>
        </div>
        <div class="post-card">
            <span class="card-tag" style="color: #d35400; background: #fae5d3;">JavaScript ES6</span>
            <h3 class="card-title">ES6+: Arrow Function, Destructuring & Template String</h3>
            <p class="card-desc">3 tính năng hiện đại giúp code JS ngắn gọn hơn. Quên cách cộng chuỗi cũ kỹ và từ khóa function đi.</p>
            <a href="/NguyenDucQui_Blog/posts/es6andfeatures/" class="read-more">Đọc tiếp</a>
        </div>
        <div class="post-card">
            <span class="card-tag" style="color: #d35400; background: #fae5d3;">JS Array</span>
            <h3 class="card-title">Bộ ba Map, Filter, Reduce: Xử lý mảng "thần thánh"</h3>
            <p class="card-desc">Cách xử lý dữ liệu trong React/Vue. Tính tổng giỏ hàng, lọc sản phẩm mà không cần vòng lặp for.</p>
            <a href="/NguyenDucQui_Blog/posts/arraymethods/" class="read-more">Đọc tiếp</a>
        </div>
        <div class="post-card">
            <span class="card-tag" style="color: #d35400; background: #fae5d3;">Async/Await</span>
            <h3 class="card-title">Bất đồng bộ: Từ Callback Hell đến Async/Await</h3>
            <p class="card-desc">Hiểu rõ về Promise và cách gọi API lấy dữ liệu người dùng chuẩn chỉ nhất trong dự án thực tế.</p>
            <a href="/NguyenDucQui_Blog/posts/asynchronousjavascript/" class="read-more">Đọc tiếp</a>
        </div>
        <div class="post-card">
            <span class="card-tag" style="color: #d35400; background: #fae5d3;">Frontend DOM</span>
            <h3 class="card-title">DOM Manipulation: JavaScript tương tác HTML</h3>
            <p class="card-desc">Sử dụng querySelector và addEventListener để bắt sự kiện click và thay đổi giao diện web động.</p>
            <a href="/NguyenDucQui_Blog/posts/dommanipulation/" class="read-more">Đọc tiếp</a>
        </div>
        <div class="post-card">
            <span class="card-tag" style="color: #d35400; background: #fae5d3;">Browser Storage</span>
            <h3 class="card-title">LocalStorage & SessionStorage: Lưu trữ dữ liệu</h3>
            <p class="card-desc">Cách lưu chế độ Dark Mode hoặc Token đăng nhập vĩnh viễn ngay trên trình duyệt của người dùng.</p>
            <a href="/NguyenDucQui_Blog/posts/localstoragesessionstorage/" class="read-more">Đọc tiếp</a>
        </div>
    </div>
</div>
