---
title: "Bộ ba 'Thần thánh' Map, Filter, Reduce: Bí kíp xử lý mảng trong JS"
date: 2025-12-24
author: "Đức Qui"
tags: ["JavaScript", "Array", "Functional Programming"]
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
Khi làm việc với các Framework hiện đại như React hay Vue, bạn sẽ rất ít khi dùng vòng lặp `for` truyền thống. Thay vào đó, chúng ta sử dụng các "Functional Array Methods". Dưới đây là 3 hàm quan trọng nhất.

Giả sử ta có danh sách sản phẩm:

```javascript
const products = [
    { id: 1, name: "Iphone 15", price: 1000, quantity: 2 },
    { id: 2, name: "Samsung S24", price: 900, quantity: 1 },
    { id: 3, name: "Op Lung", price: 10, quantity: 5 }
];
```
## 1. map() - Biến đổi mảng
Dùng khi bạn muốn tạo ra một mảng mới từ mảng cũ, nhưng thay đổi hình dạng dữ liệu.

```Java
// Tạo danh sách chỉ chứa tên sản phẩm
const productNames = products.map(item => item.name);

console.log(productNames); 
// Output: ["Iphone 15", "Samsung S24", "Op Lung"]
```
## 2. filter() - Lọc dữ liệu
Dùng khi muốn lấy ra các phần tử thỏa mãn điều kiện (giống như cái phễu).

```JavaScript

// Lọc các sản phẩm có giá trên 500$
const expensiveItems = products.filter(item => item.price > 500);

console.log(expensiveItems);
// Output: [Object Iphone, Object Samsung] (Op Lung bị loại)
```
## 3. reduce() - Gom nhóm / Tính tổng
Đây là hàm khó hiểu nhất nhưng mạnh mẽ nhất. Nó duyệt qua mảng và "cộng dồn" lại thành 1 giá trị duy nhất.

**Ví dụ:** Tính tổng tiền cả giỏ hàng Công thức: Tổng tiền = Giá * Số lượng của từng món cộng lại.

```JavaScript

// acc: biến tích lũy (accumulator) - giá trị cộng dồn
// curr: phần tử hiện tại đang duyệt
const totalBill = products.reduce((acc, curr) => {
    return acc + (curr.price * curr.quantity);
}, 0); // 0 là giá trị khởi tạo ban đầu của acc

console.log(totalBill); 
// Giải thích:
// Lượt 1: 0 + (1000 * 2) = 2000
// Lượt 2: 2000 + (900 * 1) = 2900
// Lượt 3: 2900 + (10 * 5) = 2950 -> Kết quả cuối cùng
```
</div>
<div class="btn-back-container">
    <a href="/NguyenDucQui_Blog/posts/" class="back-btn">Quay lại</a>
</div>