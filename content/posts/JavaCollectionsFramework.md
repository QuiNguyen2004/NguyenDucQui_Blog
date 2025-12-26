---
title: "Làm chủ Java Collections: Hướng dẫn cơ bản về ArrayList, HashSet và HashMap"
date: 2025-12-26
author: "Đức Qui"
tags: ["Java", "Programming", "Data Structures", "Backend"]
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
Trong lập trình Java, việc quản lý và lưu trữ dữ liệu hiệu quả là một kỹ năng cốt lõi. Khác với mảng (Array) cố định kích thước, **Java Collections Framework** cung cấp các cấu trúc dữ liệu linh hoạt, có khả năng tự động thay đổi kích thước và đi kèm với nhiều thuật toán mạnh mẽ.

Trong bài viết này, chúng ta sẽ tìm hiểu 3 class phổ biến nhất mà mọi lập trình viên Java đều phải biết: **ArrayList**, **HashSet**, và **HashMap**.

## 1. ArrayList: Mảng động linh hoạt

**ArrayList** là một triển khai của `List Interface`. Hãy tưởng tượng nó giống như một mảng bình thường, nhưng nó có thể tự động "nở ra" khi bạn thêm phần tử và "co lại" khi bạn xóa phần tử.

### Đặc điểm:
* Dữ liệu được lưu trữ có thứ tự (theo thứ tự thêm vào).
* Cho phép lưu trữ các phần tử trùng lặp.
* Truy xuất phần tử cực nhanh thông qua chỉ số (index).

### Code mẫu: Khai báo, Thêm và Xóa

```java
import java.util.ArrayList;
import java.util.List;

public class ArrayListExample {
    public static void main(String[] args) {
        // 1. Khai báo ArrayList chứa String
        // Nên sử dụng Interface 'List' ở vế trái để đảm bảo tính linh hoạt (Polymorphism)
        List<String> studentList = new ArrayList<>();

        // 2. Thêm phần tử (Add)
        studentList.add("Nguyen Van A");
        studentList.add("Tran Thi B");
        studentList.add("Le Van C");
        
        // Thêm vào vị trí cụ thể (index 1)
        studentList.add(1, "Hoang Van D");

        System.out.println("Danh sách ban đầu: " + studentList);

        // 3. Xóa phần tử (Remove)
        // Xóa theo index
        studentList.remove(0); 
        // Xóa theo đối tượng cụ thể
        studentList.remove("Le Van C");

        System.out.println("Danh sách sau khi xóa: " + studentList);

        // 4. Lấy phần tử ra (Get)
        String firstStudent = studentList.get(0);
        System.out.println("Sinh viên đầu tiên: " + firstStudent);
    }
}
```
## 2. HashSet: Tập hợp các phần tử duy nhất
HashSet là một triển khai của Set Interface. Nếu bạn muốn một danh sách đảm bảo không có phần tử nào trùng nhau, đây là lựa chọn số một.

### Đặc điểm:
Không cho phép trùng lặp (Duplicate).

Không đảm bảo thứ tự của các phần tử (thứ tự có thể thay đổi ngẫu nhiên).

Hiệu suất thêm và kiểm tra tồn tại rất cao.

### Code mẫu: Xử lý dữ liệu duy nhất
import java.util.HashSet;
import java.util.Set;
```java
public class HashSetExample {
    public static void main(String[] args) {
        // 1. Khai báo HashSet
        Set<String> emailSet = new HashSet<>();

        // 2. Thêm phần tử
        emailSet.add("user1@gmail.com");
        emailSet.add("user2@gmail.com");
        
        // Cố tình thêm phần tử trùng lặp
        boolean isAdded = emailSet.add("user1@gmail.com"); 
        
        System.out.println("Thêm trùng lặp có thành công không? " + isAdded); // Kết quả: false
        System.out.println("Danh sách Email: " + emailSet);

        // 3. Xóa phần tử
        emailSet.remove("user2@gmail.com");

        // 4. Kiểm tra tồn tại (Contains) - Rất nhanh
        if (emailSet.contains("user1@gmail.com")) {
            System.out.println("Email này đã tồn tại trong hệ thống.");
        }
    }
}
```
## 3. HashMap: Cấu trúc cặp Khóa - Giá trị (Key - Value)
HashMap là triển khai của Map Interface. Nó không lưu trữ các phần tử đơn lẻ mà lưu trữ theo cặp Key (Khóa) và Value (Giá trị). Nó giống như một cuốn từ điển: bạn dùng từ vựng (Key) để tra nghĩa (Value).

### Đặc điểm:
Key là duy nhất (không được trùng).

Value có thể trùng lặp.

Nếu thêm một Key đã tồn tại, Value cũ sẽ bị ghi đè bởi Value mới.

### Code mẫu: Thêm, Xóa và Duyệt Map
Phần quan trọng nhất của Map là cách duyệt qua các phần tử, vì nó không có chỉ số index như ArrayList.
```java
import java.util.HashMap;
import java.util.Map;

public class HashMapExample {
    public static void main(String[] args) {
        // 1. Khai báo HashMap (Key là String - Tên sản phẩm, Value là Integer - Giá tiền)
        Map<String, Integer> productPrice = new HashMap<>();

        // 2. Thêm phần tử (Put)
        productPrice.put("Laptop Dell", 15000000);
        productPrice.put("MacBook Pro", 30000000);
        productPrice.put("Mouse Logitech", 500000);

        // Cập nhật giá (Ghi đè key cũ)
        productPrice.put("Mouse Logitech", 450000);

        // 3. Xóa phần tử (Remove theo Key)
        productPrice.remove("Laptop Dell");

        System.out.println("--- Duyệt qua HashMap ---");

        // 4. CÁCH DUYỆT MAP (QUAN TRỌNG)
        // Cách tối ưu nhất: Sử dụng entrySet() để lấy cả Key và Value
        for (Map.Entry<String, Integer> entry : productPrice.entrySet()) {
            String key = entry.getKey();
            Integer value = entry.getValue();
            
            System.out.println("Sản phẩm: " + key + " - Giá: " + value + " VND");
        }        
    }
}
```

## Tổng kết: Khi nào dùng cái gì?
- **ArrayList**: Dùng khi bạn cần truy xuất dữ liệu nhanh theo vị trí (index) và danh sách ít khi phải thêm/xóa ở giữa.

- **HashSet**: Dùng khi bài toán yêu cầu dữ liệu không được trùng lặp hoặc cần kiểm tra một phần tử có tồn tại hay không cực nhanh. Lưu ý: Dữ liệu sẽ không có thứ tự.

- **HashMap**: Dùng cho các bài toán tra cứu (Lookup). Sử dụng khi bạn muốn tìm giá trị thông qua một chìa khóa (Key) cụ thể thay vì số thứ tự, ví dụ như từ điển hoặc bộ nhớ đệm (cache).
</div>
<div class="btn-back-container">
    <a href="/NguyenDucQui_Blog/posts/" class="back-btn">Quay lại</a>
</div>