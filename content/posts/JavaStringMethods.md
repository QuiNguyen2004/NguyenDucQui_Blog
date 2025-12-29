---
title: "Làm chủ Java String: 5 hàm quan trọng và Kỹ thuật tối ưu hiệu năng"
date: 2025-12-25
author: "Đức Qui"
tags: ["Java", "String", "Performance", "Tips"]
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
Trong Java, `String` là đối tượng bất biến (immutable). Điều này có nghĩa là mỗi khi bạn chỉnh sửa chuỗi, Java thực tế đang tạo ra một chuỗi mới trong bộ nhớ. Hiểu rõ các hàm xử lý chuỗi và cách tối ưu chúng là chìa khóa để viết code chuyên nghiệp.

## 1. 5 Hàm xử lý chuỗi "bất ly thân"

Dưới đây là các hàm bạn sẽ sử dụng trong 90% các dự án thực tế:

* **`length()`**: Trả về độ dài chuỗi.
* **`trim()`**: Cắt bỏ khoảng trắng thừa ở đầu và cuối chuỗi (Rất quan trọng khi xử lý input từ người dùng).
* **`substring(int beginIndex, int endIndex)`**: Cắt chuỗi con.
* **`indexOf(String str)`**: Tìm vị trí xuất hiện đầu tiên của chuỗi con (trả về -1 nếu không tìm thấy).
* **`replace(CharSequence target, CharSequence replacement)`**: Thay thế nội dung trong chuỗi.
* **`split(String regex)`**: Tách chuỗi thành mảng dựa trên ký tự phân cách (ví dụ dấu phẩy).

### Code mẫu minh họa:

```java
public class StringMethodsDemo {
    public static void main(String[] args) {
        String rawInput = "   Hello Java World   ";
        
        // 1. Làm sạch dữ liệu
        String cleanStr = rawInput.trim(); 
        System.out.println("Đã trim: [" + cleanStr + "]"); // [Hello Java World]

        // 2. Tìm kiếm và Cắt chuỗi
        int index = cleanStr.indexOf("Java");
        if (index != -1) {
            String sub = cleanStr.substring(index);
            System.out.println("Chuỗi con từ vị trí tìm thấy: " + sub); // Java World
        }

        // 3. Thay thế
        String replaced = cleanStr.replace("World", "Developer");
        System.out.println("Sau khi replace: " + replaced);

        // 4. Tách chuỗi (Split)
        String csvData = "apple,banana,orange";
        String[] fruits = csvData.split(",");
        for (String fruit : fruits) {
            System.out.println("Fruit: " + fruit);
        }
    }
}
```
## 2. Mẹo hiệu năng: Tại sao phải dùng StringBuilder?
Vì String là bất biến, đoạn code sau là một "thảm họa" về hiệu năng:
```java
String s = "";
for (int i = 0; i < 1000; i++) {
    s = s + i; // TẠO RA 1000 ĐỐI TƯỢNG STRING MỚI trong bộ nhớ!
}
```
****Giải pháp**: Sử dụng **StringBuilder** (hoặc **StringBuffer** cho đa luồng). Nó cho phép sửa đổi chuỗi trực tiếp mà không tạo đối tượng rác.
```java
StringBuilder sb = new StringBuilder();
for (int i = 0; i < 1000; i++) {
    sb.append(i); // Chỉ thao tác trên một đối tượng duy nhất
}
String finalString = sb.toString();
```
**Quy tắc vàng**: Dùng cộng chuỗi (+) cho các nối chuỗi đơn giản, ít lặp. Dùng StringBuilder cho các vòng lặp hoặc xử lý chuỗi phức tạp.

## 3. Cạm bẫy "chết người": So sánh chuỗi bằng ==
Đây là lỗi phổ biến nhất mà lập trình viên mới thường mắc phải. Trong Java:

- **==:** So sánh địa chỉ ô nhớ **(Reference)**.

- **.equals():** So sánh nội dung của chuỗi **(Value)**.

Vì String là đối tượng (Object), bạn TUYỆT ĐỐI KHÔNG được dùng == để kiểm tra nội dung văn bản, đặc biệt là khi chuỗi được tạo từ new String() hoặc nhận từ input người dùng.
```java
String s1 = new String("Hello");
String s2 = new String("Hello");

// SAI: So sánh địa chỉ bộ nhớ (sẽ trả về false vì là 2 object khác nhau trong Heap)
if (s1 == s2) { 
    System.out.println("Hai chuỗi bằng nhau"); 
} else {
    System.out.println("Hai chuỗi KHÁC nhau"); // Code sẽ chạy vào đây
}

// ĐÚNG: So sánh nội dung chữ
if (s1.equals(s2)) {
    System.out.println("Nội dung giống nhau"); // Code sẽ chạy vào đây
}
```
- **Mẹo nhỏ**: Nếu bạn muốn so sánh không phân biệt hoa thường (ví dụ check username đăng nhập: "Admin" và "admin"), hãy dùng **.equalsIgnoreCase()**.
## 4. Các tính năng hiện đại (Java 11+)
Nếu dự án của bạn đang chạy trên Java 11 trở lên, bạn có thêm những "vũ khí" rất tiện lợi mà không cần viết logic thủ công:

- **isBlank():** Kiểm tra chuỗi rỗng HOẶC chỉ chứa toàn khoảng trắng (Thông minh hơn **isEmpty()** cũ kỹ).

- **repeat(int count):** Lặp lại chuỗi n lần.

- **lines():** Chia chuỗi thành một Stream các dòng (cực tiện khi xử lý văn bản nhiều dòng).
```java
String input = "   ";
System.out.println(input.isEmpty()); // false (vì có dấu cách)
System.out.println(input.isBlank()); // true (Java 11: hiểu là chuỗi trống)

String star = "*";
System.out.println(star.repeat(5)); // In ra: *****
```
## 5. Bí mật về "String Pool" (Vùng nhớ hằng chuỗi)
Bạn có bao giờ thắc mắc tại sao chúng ta hiếm khi thấy ai viết **String s = new String("Hello")**; không? Đó là vì Java có một cơ chế tối ưu bộ nhớ cực hay gọi là **String Pool**.

**Cách hoạt động:** Khi bạn tạo chuỗi bằng dấu ngoặc kép **String s = "Hello"**;, Java sẽ kiểm tra trong "bể chứa" (Pool) xem đã có chuỗi "Hello" chưa.

- Nếu có rồi: Nó trả về tham chiếu tới chuỗi cũ (Tiết kiệm RAM).

- Nếu chưa: Nó tạo mới và bỏ vào Pool.

**Ngược lại:** Nếu dùng new String("Hello"), bạn ép Java tạo ra một đối tượng hoàn toàn mới trong bộ nhớ Heap, bỏ qua cơ chế Pool. Điều này gây lãng phí.

Lời khuyên: Luôn ưu tiên cách khai báo trực tiếp (String s = "...") thay vì dùng từ khóa new.
## 6. Text Blocks (Java 15+): Cứu tinh cho SQL và JSON
Trước đây, nếu bạn muốn gán một chuỗi HTML, JSON hoặc câu lệnh SQL dài vào biến **String**, bạn phải đối mặt với "cơn ác mộng" của việc nối chuỗi và ký tự thoát (\n, \").

**Java 15** (chính thức) đã giới thiệu Text Blocks (sử dụng 3 dấu ngoặc kép """).

Cách cũ (Rất rối mắt):
```java
String json = "{\n" +
              "  \"name\": \"John\",\n" +
              "  \"age\": 30\n" +
              "}";
```
Cách mới với Text Blocks (Sạch sẽ, dễ đọc):
```java
String json = """
              {
                  "name": "John",
                  "age": 30
              }
              """;
```
## 7. String.format(): Định dạng chuỗi chuyên nghiệp
Thay vì cộng chuỗi thủ công để tạo ra một câu thông báo phức tạp (ví dụ: hiển thị giá tiền, ngày tháng), hãy dùng **String.format()**. Nó giúp code của bạn giống như một mẫu **(template)** dễ quản lý.

```Java

String product = "Laptop";
double price = 1500.50;

// Cách "nông dân" (Khó đọc, dễ sai sót khoảng trắng)
String msg1 = "Sản phẩm " + product + " có giá là " + price + " USD";

// Cách "chuyên gia" (Dễ nhìn, định dạng được số thập phân)
// %s: chuỗi, %.2f: số thực lấy 2 số sau dấu phẩy
String msg2 = String.format("Sản phẩm %s có giá là %.2f USD", product, price);

System.out.println(msg2); // Output: Sản phẩm Laptop có giá là 1500.50 USD
```
## 8. Đừng "tự chế xe đạp": Hãy dùng thư viện (Bonus)
Trong môi trường doanh nghiệp **(Enterprise)**, việc xử lý null là rất quan trọng để tránh lỗi NullPointerException. Thay vì viết **if (str != null && str.length() > 0)**, các lập trình viên kinh nghiệm thường dùng thư viện **Apache Commons Lang** với **class StringUtils.**

- **StringUtils.isEmpty(str):** Kiểm tra rỗng an toàn (không bị lỗi ngay cả khi str là null).

- **StringUtils.capitalize(str):** Viết hoa chữ cái đầu.

```Java

    // Ví dụ thực tế
    String input = null;

    // if (input.trim().isEmpty()) -> Sẽ BỊ LỖI NullPointerException ngay lập tức!

    // Dùng thư viện: An toàn tuyệt đối
    if (StringUtils.isBlank(input)) {
        System.out.println("Chuỗi rỗng hoặc null");
    }
```
## Tổng kết
- Chuỗi **(String)** tuy đơn giản nhưng chứa đựng nhiều vấn đề về hiệu năng và bộ nhớ. Hãy ghi nhớ 3 điều cốt lõi để code "xịn" hơn:

- Luôn dùng **.equals()** để so sánh nội dung.

- Dùng **StringBuilder** khi cần cộng gộp chuỗi nhiều lần (đặc biệt trong vòng lặp).

- Luôn xử lý đầu vào bằng **trim()** hoặc **isBlank()** để tránh lỗi logic do thừa khoảng trắng.
</div>
<div class="btn-back-container">
    <a href="/NguyenDucQui_Blog/posts/" class="back-btn">Quay lại</a>
</div>