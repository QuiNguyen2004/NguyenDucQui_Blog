---
title: "Asynchronous JavaScript: Từ Callback Hell đến Async/Await hiện đại"
date: 2025-12-07
author: "Đức Qui"
tags: ["JavaScript", "Async", "Promise", "API"]
categories: ["Tutorial"]
---
<style>
    /* Container chính giới hạn chiều rộng và căn giữa */
    .post-container {
        max-width: 800px;
        margin: 30px auto;
        padding: 20px;
        font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
        line-height: 1.7;
        color: #333;
        background-color: #fff;
        box-shadow: 0 0 20px rgba(0,0,0,0.05);
        border-radius: 12px;
    }

    /* Style cho nút Quay lại */
    .back-btn {
        display: inline-flex;
        align-items: center;
        text-decoration: none;
        color: #fff !important;
        background-color: #2c3e50;
        padding: 8px 15px;
        border-radius: 20px;
        font-weight: 600;
        font-size: 0.9rem;
        transition: all 0.3s ease;
        margin-bottom: 20px;
    }
    .back-btn:hover {
        background-color: #34495e;
        transform: translateX(-5px);
    }
    .back-btn::before {
        content: "←";
        margin-right: 8px;
        font-size: 1.2rem;
    }

    /* Tiêu đề */
    .post-container h1 { color: #2c3e50; font-size: 2.2rem; margin-bottom: 10px; }
    .post-container h2 { 
        color: black; /* Màu cam nổi bật cho tiêu đề phụ */
        border-bottom: 2px solid #f0f2f5;
        padding-bottom: 10px;
        margin-top: 40px;
    }

    /* Đoạn văn */
    .post-container p { margin-bottom: 20px; }
    
    /* Inline code (ví dụ: single-threaded) */
    .post-container p code, li code {
        background-color: #f8f9fa;
        color: #d63031;
        padding: 2px 6px;
        border-radius: 4px;
        font-family: 'Fira Code', monospace;
        font-size: 0.9em;
    }

    /* Khối Code block (Pre) */
    .post-container pre {
        background-color: #1e1e1e !important; /* Nền tối màu chuẩn dev */
        color: #d4d4d4;
        padding: 20px;
        border-radius: 8px;
        overflow-x: auto; /* Thanh cuộn ngang nếu code quá dài */
        box-shadow: inset 0 0 10px rgba(0,0,0,0.2);
        border: 1px solid #333;
    }
    .post-container pre code {
        background-color: transparent !important;
        color: inherit;
        padding: 0;
    }

    /* Phần trích dẫn (Blockquote) cho Quy tắc */
    .post-container blockquote {
        background-color: #e8f4fd;
        border-left: 5px solid #3498db;
        margin: 30px 0;
        padding: 15px 20px;
        color: #2c3e50;
        font-style: italic;
        border-radius: 0 8px 8px 0;
    }
    .post-container blockquote strong {
        color: #d35400;
    }
</style>

<div class="post-container">
JavaScript là ngôn ngữ đơn luồng (single-threaded). Điều này có nghĩa là nó chỉ làm một việc tại một thời điểm. Vậy làm sao nó xử lý được các tác vụ tốn thời gian như gọi API, đọc file mà không làm treo trình duyệt? Đó là nhờ cơ chế **Bất đồng bộ (Asynchronous)**.

## 1. Quá khứ: Callback Hell
Ngày xưa, chúng ta truyền hàm vào trong hàm. Nếu logic phức tạp, code sẽ lồng nhau chằng chịt hình tháp, gọi là "Callback Hell".

```javascript
getData(function(a) {
    getMoreData(a, function(b) {
        getMoreData(b, function(c) {
            // Rất khó đọc và debug!
        });
    });
});
```
## 2. Hiện tại: Promise và Async/Await
ES6 giới thiệu Promise để xử lý chuỗi bất đồng bộ tốt hơn, và ES8 mang đến Async/Await giúp viết code bất đồng bộ trông y hệt code đồng bộ tuần tự.

**Code mẫu:** Gọi API lấy dữ liệu user
Sử dụng fetch (có sẵn trong trình duyệt) kết hợp async/await.

```JavaScript

// Khai báo hàm bất đồng bộ với từ khóa 'async'
const fetchUserData = async () => {
    try {
        console.log("Đang tải dữ liệu...");
        
        // Từ khóa 'await': Tạm dừng code tại đây đợi API trả về kết quả
        const response = await fetch('[https://jsonplaceholder.typicode.com/users/1](https://jsonplaceholder.typicode.com/users/1)');
        
        // Đợi chuyển đổi kết quả sang JSON
        const data = await response.json();
        
        console.log("Thành công!", data);
        console.log("Tên user:", data.name);
        
    } catch (error) {
        // Bắt lỗi nếu gọi API thất bại (mất mạng, server lỗi...)
        console.error("Lỗi rồi:", error);
    }
};

// Chạy hàm
fetchUserData();
```
**Quy tắc:** await chỉ được dùng bên trong một hàm async. Đây là cách chuẩn mực để gọi API trong các dự án thực tế hiện nay.
</div>
<div class="btn-back-container">
    <a href="/NguyenDucQui_Blog/posts/" class="back-btn">Quay lại </a>
</div>