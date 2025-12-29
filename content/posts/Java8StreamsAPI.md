---
title: "Java 8 Streams API: Tạm biệt vòng lặp for, chào đón code hiện đại"
date: 2025-12-25
author: "Đức Qui"
tags: ["Java", "Stream API", "Functional Programming", "Backend"]
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
Nếu như Collections Framework (Bài 1) giúp bạn lưu trữ dữ liệu, thì **Streams API** (ra mắt từ Java 8) chính là công cụ mạnh mẽ để **xử lý** đống dữ liệu đó.

Trước Java 8, để lọc hay biến đổi dữ liệu, chúng ta phải viết những vòng lặp `for` dài dòng. Với Streams, bạn viết code giống như đang viết câu lệnh SQL: mô tả **bạn muốn gì**, thay vì mô tả **phải làm từng bước thế nào**.

## 1. So sánh: Vòng lặp truyền thống vs. Streams

Hãy xem bài toán: *Cho một danh sách tên, hãy lọc ra các tên bắt đầu bằng chữ 'A', chuyển chúng thành chữ in hoa và lưu vào danh sách mới.*

### Cách cũ (Java 7 trở về trước)
Bạn phải tự tạo list tạm, tự viết vòng lặp, tự kiểm tra điều kiện `if`.

```java
List<String> names = Arrays.asList("An", "Binh", "Anh", "Cuong", "Dat");
List<String> result = new ArrayList<>();

for (String name : names) {
    if (name.startsWith("A")) {           // 1. Lọc
        String upperName = name.toUpperCase(); // 2. Chuyển đổi
        result.add(upperName);            // 3. Gom nhóm
    }
}
System.out.println(result); // Output: [AN, ANH]
```
### Cách mới (Java 8 Streams)
Code đọc như văn xuôi: "Lấy danh sách -> Lọc chữ A -> Chuyển in hoa -> Gom lại".
```java
List<String> result = names.stream()
    .filter(name -> name.startsWith("A"))  // 1. Lọc
    .map(name -> name.toUpperCase())       // 2. Chuyển đổi
    .collect(Collectors.toList());         // 3. Gom nhóm

System.out.println(result); // Output: [AN, ANH]
```
## 2. Các thao tác cốt lõi trong Stream
Stream hoạt động như một dây chuyền nhà máy: Nguyên liệu đi vào -> Qua các máy chế biến -> Ra thành phẩm.

### A. Filter (Lọc dữ liệu)
filter() chấp nhận một điều kiện (Predicate). Chỉ những phần tử thỏa mãn điều kiện mới được đi tiếp qua "cửa" này.
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6);

// Lọc lấy số chẵn
List<Integer> evenNumbers = numbers.stream()
                                   .filter(n -> n % 2 == 0)
                                   .collect(Collectors.toList());
// Kết quả: [2, 4, 6]
```
### B. Map (Chuyển đổi dữ liệu)
**map()** dùng để biến đổi phần tử từ dạng này sang dạng khác (ví dụ: từ số sang chữ, từ đối tượng User sang String email, hoặc tính toán lại giá trị). Số lượng phần tử đầu ra bằng số lượng phần tử đầu vào.

```Java
List<String> words = Arrays.asList("java", "stream", "api");

// Chuyển đổi từ chuỗi sang độ dài của chuỗi
List<Integer> lengths = words.stream()
                             .map(s -> s.length()) // "java" -> 4
                             .collect(Collectors.toList());
// Kết quả: [4, 6, 3]
```
### C. Collect (Gom nhóm kết quả)
Các thao tác như **filter** hay **map** được gọi là Intermediate Operations (trung gian), chúng chưa chạy ngay cho đến khi gặp một Terminal Operation (kết thúc) như **collect**.

**collect()** đóng gói dòng dữ liệu đã xử lý về lại các cấu trúc dữ liệu quen thuộc như **List, Set,** hoặc **Map**.
```java
// Gom về List
List<String> list = stream.collect(Collectors.toList());

// Gom về Set (để loại bỏ trùng lặp nếu có)
Set<String> set = stream.collect(Collectors.toSet());

// Gom về chuỗi duy nhất (nối các phần tử)
String joined = stream.collect(Collectors.joining(", "));
```
## D. Sorted (Sắp xếp dữ liệu)
Thay vì dùng **Collections.sort()** bên ngoài, bạn có thể sắp xếp ngay trong dòng chảy dữ liệu.

```Java
List<String> names = Arrays.asList("Cuong", "An", "Binh");

// 1. Sắp xếp mặc định (A -> Z)
List<String> sortedNames = names.stream()
    .sorted() 
    .collect(Collectors.toList()); 
// Kết quả: [An, Binh, Cuong]

// 2. Sắp xếp tùy chỉnh (Ví dụ: Theo độ dài chuỗi, từ ngắn đến dài)
List<String> byLength = names.stream()
    .sorted((s1, s2) -> s1.length() - s2.length())
    .collect(Collectors.toList());
```
## E. Distinct & Limit (Lọc trùng và Giới hạn)
Hai hàm này cực kỳ hữu ích khi làm chức năng phân trang **(pagination)** hoặc loại bỏ dữ liệu rác.

```Java

List<Integer> numbers = Arrays.asList(1, 2, 2, 3, 4, 4, 5);

// Lấy 3 số đầu tiên KHÔNG trùng nhau
List<Integer> result = numbers.stream()
    .distinct()  // Loại bỏ số trùng -> [1, 2, 3, 4, 5]
    .limit(3)    // Chỉ lấy 3 số đầu -> [1, 2, 3]
    .collect(Collectors.toList());
```
## 3. Các thao tác kết thúc (Terminal Operations) khác
Ngoài collect(), Stream còn có nhiều cách khác để "chốt đơn" dữ liệu. Hãy nhớ: Nếu không có Terminal Operation, Stream sẽ không chạy!

### A. forEach (Duyệt và thực thi)
Dùng khi bạn muốn làm gì đó với từng phần tử (ví dụ: in ra màn hình, lưu vào DB) mà không cần trả về danh sách mới.

```Java

List<String> names = Arrays.asList("An", "Binh", "Cuong");
// In từng tên ra màn hình
names.stream().forEach(name -> System.out.println("Xin chào " + name));
```
### B. count, min, max (Thống kê)
```Java

long count = names.stream().filter(n -> n.length() > 3).count();

// Tìm số nhỏ nhất
Optional<Integer> min = numbers.stream().min(Integer::compare);
```
### C. anyMatch, allMatch, noneMatch (Kiểm tra điều kiện)
Trả về boolean. Rất nhanh vì nó sử dụng cơ chế **Short-circuiting** (ngắt mạch - ví dụ tìm thấy một cái sai là dừng ngay, không cần duyệt hết).

```Java

boolean hasAn = names.stream().anyMatch(n -> n.equals("An")); // True nếu có ít nhất 1 người tên An
boolean allShort = names.stream().allMatch(n -> n.length() < 10); // True nếu TẤT CẢ đều ngắn hơn 10 ký tự
```
## 4. Cơ chế "Lazy Evaluation" (Đánh giá lười) - Bí mật hiệu năng
Đây là điểm "ăn tiền" của Stream so với vòng lặp for truyền thống.

Hãy xem đoạn code sau:

```Java

names.stream()
     .filter(n -> {
         System.out.println("Đang lọc: " + n);
         return n.length() > 3;
     })
     .map(n -> {
         System.out.println("Đang map: " + n);
         return n.toUpperCase();
     })
     .limit(2)
     .collect(Collectors.toList());
```
Điều gì xảy ra? Stream thông minh đến mức nó sẽ kết hợp các bước lại. Ngay khi tìm đủ 2 phần tử (limit(2)), nó sẽ DỪNG NGAY LẬP TỨC, không thèm xử lý các phần tử còn lại trong danh sách.

Vòng lặp For cũ: Thường sẽ duyệt hết danh sách rồi mới cắt lấy 2 phần tử (lãng phí).

**Stream:** Chỉ làm đúng mức cần thiết.

## 5. Parallel Streams (Đa luồng) - Vũ khí hạng nặng
Nếu bạn có một danh sách 1 triệu phần tử, xử lý tuần tự **(Sequential)**sẽ lâu. Stream cho phép bạn bật chế độ "đa luồng" cực dễ chỉ bằng cách thay **stream()** thành **parallelStream().**

```Java

// Java sẽ tự động chia nhỏ list ra và xử lý trên nhiều lõi CPU cùng lúc
long count = bigList.parallelStream()
    .filter(e -> e.isActive())
    .count();
```
**⚠️ Cảnh báo:**Chỉ dùng parallelStream khi dữ liệu thực sự lớn và các tác vụ độc lập nhau. Nếu dùng bừa bãi cho list nhỏ, chi phí quản lý luồng sẽ làm code chạy chậm hơn cả cách thường!
## Tổng kết nhanh
Tại sao bạn nên dùng Streams thay vì vòng lặp for?

- Code ngắn gọn: Giảm thiểu code thừa (boilerplate code).

- Dễ đọc hiểu: Logic xử lý hiện rõ ràng theo dòng chảy (Flow).

- Không thay đổi dữ liệu gốc: Stream tạo ra kết quả mới, không làm biến đổi List ban đầu.

- Hỗ trợ song song (Parallel): Dễ dàng xử lý đa luồng với parallelStream() mà không cần code phức tạp.
</div>
<div class="btn-back-container">
    <a href="/NguyenDucQui_Blog/posts/" class="back-btn">Quay lại</a>
</div>