---
title: "LocalStorage và SessionStorage: Lưu dữ liệu ngay trên trình duyệt"
date: 2025-12-25
author: "Đức Qui"
tags: ["JavaScript", "Storage", "Cookies"]
categories: ["Tutorial"]
ShowToc: true
TocOpen: true
hidemeta: false
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
Bạn muốn lưu giữ trạng thái "Đã đăng nhập" hoặc chế độ "Dark Mode" ngay cả khi người dùng F5 tải lại trang? Trình duyệt cung cấp cho chúng ta **Web Storage API**.

## 1. Phân biệt LocalStorage và SessionStorage

| Đặc điểm | LocalStorage | SessionStorage |
| :--- | :--- | :--- |
| **Thời gian sống** | **Vĩnh viễn** (đến khi code xóa hoặc user xóa cache). | **Tạm thời** (mất ngay khi đóng Tab/Trình duyệt). |
| **Phạm vi** | Chung cho cả domain. | Riêng biệt cho từng Tab. |
| **Dung lượng** | Khoảng 5MB-10MB. | Khoảng 5MB. |

## 2. Cách sử dụng (Giống hệt nhau)

Chúng ta có 4 hàm cơ bản: `setItem`, `getItem`, `removeItem`, `clear`.

### Ví dụ 1: Lưu chế độ Dark Mode (Dữ liệu đơn giản)

```javascript
// 1. Lưu dữ liệu
localStorage.setItem('theme', 'dark');

// 2. Lấy dữ liệu
const currentTheme = localStorage.getItem('theme');
if (currentTheme === 'dark') {
    document.body.classList.add('dark-mode');
}

// 3. Xóa dữ liệu
// localStorage.removeItem('theme');
```
### Ví dụ 2: Lưu Object (Quan trọng)
Storage chỉ lưu được Chuỗi (String). Nếu bạn muốn lưu một Object (ví dụ thông tin User), bạn phải ép kiểu sang JSON string.

```JavaScript

const userProfile = {
    id: 1,
    name: "Duc Qui",
    role: "Admin"
};

// SAI: localStorage.setItem('user', userProfile); -> Kết quả: "[object Object]"

// ĐÚNG: Dùng JSON.stringify
localStorage.setItem('user', JSON.stringify(userProfile));

// KHI LẤY RA: Dùng JSON.parse để chuyển lại thành Object
const storedUser = localStorage.getItem('user');
if (storedUser) {
    const userData = JSON.parse(storedUser);
    console.log("Chào mừng quay lại, " + userData.name);
}
```
</div>
<div class="btn-back-container">
    <a href="/NguyenDucQui_Blog/posts/" class="back-btn">Quay lại</a>
</div>