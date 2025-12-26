---
title: "Đọc ghi file trong Java: Quên cách cũ đi, hãy dùng Java NIO"
date: 2025-12-25
author:  "Đức Qui"
tags: ["Java", "IO", "NIO", "File"]
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
Trước đây, để đọc một file text, chúng ta phải dùng `FileReader`, `BufferedReader` bọc nhau rất rườm rà. Kể từ Java 7 (và hoàn thiện ở Java 8), gói `java.nio.file` (New IO) giúp thao tác file trở nên cực kỳ đơn giản.

## 1. Các class cốt lõi của Java NIO

* **`Path`**: Đại diện cho đường dẫn file (thay thế cho `File` cũ).
* **`Paths`**: Class tiện ích để tạo đối tượng `Path`.
* **`Files`**: Class chứa các phương thức static mạnh mẽ để thao tác file (đọc, ghi, copy, delete...).

## 2. Đọc file nhanh với `Files.readAllLines`

Phương thức này đọc toàn bộ nội dung file và trả về một `List<String>`, mỗi phần tử là một dòng.

### Code mẫu: Đọc và Ghi file

```java
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.Paths;
import java.nio.file.StandardOpenOption;
import java.io.IOException;
import java.util.List;

public class FileManager {
    public static void main(String[] args) {
        // 1. Định nghĩa đường dẫn file
        // "." đại diện cho thư mục hiện tại của project
        Path path = Paths.get("./data.txt");

        // Dữ liệu mẫu để ghi
        String content = "Hello Java NIO\nViết file thật dễ dàng!";

        try {
            // 2. Ghi file (Tạo mới nếu chưa có, hoặc ghi đè)
            Files.write(path, content.getBytes());
            System.out.println("Ghi file thành công!");

            // 3. Đọc file (Cách hiện đại)
            List<String> lines = Files.readAllLines(path);
            
            System.out.println("--- Nội dung file ---");
            // Kết hợp với Lambda Expression (Bài 2) để in ra
            lines.forEach(line -> System.out.println(line));

        } catch (IOException e) {
            System.out.println("Có lỗi khi thao tác file: " + e.getMessage());
        }
    }
}
```
## 3. Xử lý file lớn (Big Data) với Files.lines
Để đọc file lớn an toàn, chúng ta sử dụng Files.lines(path). Phương thức này trả về một Stream<String>. Nó hoạt động theo cơ chế Lazy Loading (cần đến đâu đọc đến đó), giúp bộ nhớ luôn nhẹ nhàng dù file có nặng cả chục GB.
```java
// Cách đọc file lớn chuẩn kỹ sư Backend
// Sử dụng Try-with-resources để tự động đóng file sau khi đọc xong
try (Stream<String> stream = Files.lines(path)) {
    
    stream.filter(line -> line.contains("ERROR")) // Chỉ lọc lấy dòng lỗi
          .forEach(System.out::println);          // In ra màn hình

} catch (IOException e) {
    e.printStackTrace();
}
```
## 4. Các thao tác quản lý file phổ biến
Ngoài đọc/ghi, Files còn cung cấp bộ công cụ "dao đa năng" để bạn quản lý tập tin và thư mục chỉ với 1 dòng code:
```java 
public static void fileOperationsDemo() throws IOException {
    Path source = Paths.get("./data.txt");
    Path backup = Paths.get("./data_backup.txt");

    // 1. Kiểm tra file có tồn tại không trước khi làm việc
    if (Files.exists(source)) {
        
        // 2. Copy file (thêm option REPLACE_EXISTING để ghi đè nếu file kia đã có)
        Files.copy(source, backup, StandardCopyOption.REPLACE_EXISTING);
        System.out.println("Đã backup file thành công!");

        // 3. Xóa file gốc
        Files.delete(source);
        System.out.println("Đã xóa file gốc.");
    }
}
```
## Tổng kết
Chuyển đổi từ java.io.File sang java.nio.file là bước đi cần thiết để code của bạn hiện đại và hiệu quả hơn.

- Dùng Files.readAllLines cho file cấu hình, file text nhỏ.

- Dùng Files.lines (kết hợp Stream) cho file log, dữ liệu lớn.

- Tận dụng sức mạnh của class Files để copy, move, delete thay vì viết thủ công.
</div>
<div class="btn-back-container">
    <a href="/NguyenDucQui_Blog/posts/" class="back-btn">Quay lại</a>
</div>