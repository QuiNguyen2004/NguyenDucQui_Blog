---
title: "DOM Manipulation: Cách JavaScript 'nói chuyện' với HTML"
date: 2025-12-25
author: "Đức Qui"
tags: ["JavaScript", "DOM", "Frontend"]
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
Để làm website "động" (click nút thì hiện popup, đổi màu...), JavaScript cần thao tác với DOM (Document Object Model). Dưới đây là các lệnh cơ bản nhất.

## 1. Truy xuất phần tử (Selectors)

**`document.getElementById('id')`**: Lấy theo ID (nhanh nhất).
**`document.querySelector('.class')`**: Lấy phần tử đầu tiên khớp với CSS Selector (Rất linh hoạt).
**`document.querySelectorAll('p')`**: Lấy tất cả các thẻ p.

## 2. Lắng nghe sự kiện (Event Listener)

Đừng gán `onclick` trực tiếp vào HTML nữa, hãy dùng `addEventListener` để code JS tách biệt và sạch sẽ.

```html
<button id="btn-login">Đăng nhập</button>
<div id="box" style="width: 100px; height: 100px; background: red;"></div>
```
```JavaScript

// JavaScript
const btn = document.querySelector('#btn-login');
const box = document.querySelector('#box');

btn.addEventListener('click', function() {
    alert("Bạn đã click nút Đăng nhập!");
    
    // Thay đổi màu cái hộp bên dưới
    box.style.backgroundColor = "blue";
});
```
## 3. Thao tác Class (CSS)
Thay vì sửa style trực tiếp, chuyên nghiệp hơn là thêm/xóa class CSS.

```CSS
/* CSS */
.dark-mode {
    background-color: black;
    color: white;
}
```
```JavaScript

// JS: Toggle class (Có thì xóa, chưa có thì thêm)
document.body.classList.toggle('dark-mode');
```
</div>
<div class="btn-back-container">
    <a href="/NguyenDucQui_Blog/posts/" class="back-btn">Quay lại</a>
</div>