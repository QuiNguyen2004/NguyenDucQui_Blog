---
title: "JavaScript ES6+: 3 Tính năng 'nhỏ nhưng có võ' bạn phải biết"
date: 2025-12-25
author: "Đức Qui"
tags: ["JavaScript", "ES6", "Frontend", "Tips"]
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
Kể từ phiên bản ES6 (2015), JavaScript đã lột xác hoàn toàn. Nếu bạn vẫn đang viết code theo kiểu cũ, bạn đang bỏ lỡ những cú pháp giúp code ngắn gọn và "sạch" hơn gấp nhiều lần. Hôm nay, chúng ta sẽ tìm hiểu 3 tính năng được sử dụng nhiều nhất: **Arrow Functions**, **Destructuring** và **Template Literals**.

## 1. Arrow Functions (`=>`)

Đây là cách viết hàm ngắn gọn hơn, bỏ đi từ khóa `function` rườm rà.

### So sánh:

**Cách cũ (ES5):**
```javascript
function sum(a, b) {
    return a + b;
}
```
**Cách mới (Arrow Function):**

```JavaScript
    // Nếu hàm chỉ có 1 dòng return, bạn có thể bỏ luôn dấu ngoặc nhọn {} và từ khóa return
    const sum = (a, b) => a + b;
    // Hàm có 1 tham số thì không cần ngoặc tròn ()
    const square = x => x * x;
```
Lưu ý: Arrow Function không chỉ giúp viết ngắn hơn mà còn xử lý từ khóa this khác với hàm thường (chúng ta sẽ bàn kỹ hơn ở các bài nâng cao).
## 2. Template Literals (Chuỗi nội suy)
Quên đi ác mộng cộng chuỗi bằng dấu +. Hãy dùng dấu backtick (`) và cú pháp ${biến}.
**Cách cũ:**
```JavaScript
var name = "Qui";
var message = "Xin chào, " + name + "! Chào mừng bạn.";
```
**Cách mới:**
```JavaScript
const name = "Qui";
const message = `Xin chào, ${name}! 
Chào mừng bạn đến với thế giới ES6.
(Bạn thậm chí có thể xuống dòng thoải mái)`;
```
## 3. Destructuring (Phân rã biến)
Giúp bạn "móc" dữ liệu từ Array hoặc Object ra các biến riêng biệt cực nhanh.

**Với Object:**

```JavaScript

const user = { 
    fullName: "Nguyen Van A", 
    age: 25, 
    role: "Admin" 
};

// Cách cũ:
// const name = user.fullName;
// const age = user.age;

// Cách mới:
const { fullName, age } = user; 
System.out.println(fullName); // "Nguyen Van A"
```
**Với Array:**

```JavaScript

const colors = ["Red", "Green", "Blue"];
const [first, second] = colors;

console.log(first); // "Red"
```
</div>
<div class="btn-back-container">
    <a href="/NguyenDucQui_Blog/posts/" class="back-btn">Quay lại</a>
</div>