---
title: "Java Exception Handling: Bắt lỗi chuyên nghiệp với Try-Catch và Multi-catch"
date: 2025-12-25
author: "Đức Qui"
tags: ["Java", "Exception", "Error Handling"]
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
Lỗi (Bug) là điều không thể tránh khỏi. Thay vì để ứng dụng "sập" (crash) trước mặt người dùng, Java cung cấp cơ chế `try-catch` để xử lý tình huống ngoại lệ một cách duyên dáng.

## 1. Cấu trúc cơ bản: Try - Catch - Finally

* **Try:** Chứa đoạn code "nguy hiểm" có khả năng gây lỗi.
* **Catch:** Nơi xử lý khi lỗi xảy ra.
* **Finally:** Code trong khối này **LUÔN LUÔN** chạy, dù có lỗi hay không (Thường dùng để đóng kết nối DB, đóng file).

## 2. Phân biệt `throw` và `throws`

* **`throw`**: Hành động ném ra một lỗi cụ thể (Dùng bên trong thân hàm).
    * Ví dụ: `if (age < 18) throw new ArithmeticException("Chưa đủ tuổi");`
* **`throws`**: Khai báo rằng hàm này *có thể* gây ra lỗi, người gọi hàm phải tự xử lý (Dùng ở chữ ký hàm).
    * Ví dụ: `public void readFile() throws IOException { ... }`

## 3. Tính năng Multi-catch (Java 7+)

Trước đây, nếu muốn bắt nhiều lỗi, bạn phải viết nhiều khối `catch` lặp lại code. Từ Java 7, bạn có thể gộp chúng lại bằng dấu `|`.

### Code mẫu tổng hợp:

```java
import java.util.Scanner;
import java.util.InputMismatchException;

public class ExceptionDemo {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        try {
            System.out.print("Nhập số chia: ");
            int divisor = scanner.nextInt();
            
            // Có thể gây lỗi chia cho 0
            int result = 100 / divisor; 
            System.out.println("Kết quả: " + result);

            // Giả sử có một mảng
            int[] arr = {1, 2};
            System.out.println(arr[10]); // Lỗi truy cập ngoài mảng

        } catch (ArithmeticException | ArrayIndexOutOfBoundsException e) {
            // MULTI-CATCH: Bắt cả lỗi toán học và lỗi mảng ở đây
            System.out.println("Lỗi tính toán hoặc truy cập mảng: " + e.getMessage());
            
        } catch (InputMismatchException e) {
            // Bắt lỗi nhập sai kiểu dữ liệu (nhập chữ thay vì số)
            System.out.println("Vui lòng chỉ nhập số nguyên!");
            
        } catch (Exception e) {
            // Bắt tất cả các lỗi còn lại (Trùm cuối)
            System.out.println("Lỗi không xác định: " + e.toString());
            
        } finally {
            // Luôn chạy để dọn dẹp
            System.out.println("Kết thúc chương trình, đóng Scanner.");
            scanner.close();
        }
    }
}
```
## 4. Try-with-resources (Java 7+): Quên đi nỗi lo rò rỉ bộ nhớ
Ở ví dụ trên, chúng ta phải dùng khối finally để đóng Scanner. Nếu bạn mở kết nối Database, mở File, mở Network... bạn sẽ có hàng tá dòng code close() trong finally, rất rối rắm và dễ quên.

- Try-with-resources cho phép khai báo tài nguyên ngay trong dấu ngoặc tròn try(...). Java sẽ tự động đóng chúng khi khối try kết thúc (dù có lỗi hay không).
```java
// Cú pháp: try (Khai báo tài nguyên cần tự đóng ở đây)
try (Scanner scanner = new Scanner(System.in)) {
    
    System.out.print("Nhập số: ");
    int number = scanner.nextInt();
    System.out.println("Bạn đã nhập: " + number);

    // KHÔNG CẦN viết finally để scanner.close() nữa!
    // Java tự làm việc đó cho bạn.

} catch (Exception e) {
    e.printStackTrace();
}
```
## 5 Tạo Custom Exception (Ngoại lệ tự định nghĩa)
- Đôi khi các lỗi có sẵn của Java không mô tả đúng nghiệp vụ của bạn (ví dụ: lỗi "Số dư tài khoản không đủ"). Lúc này, bạn cần tạo Exception riêng.
```java
// 1. Tạo class lỗi riêng, kế thừa Exception (nếu muốn bắt buộc xử lý)
class NotEnoughMoneyException extends Exception {
    public NotEnoughMoneyException(String message) {
        super(message);
    }
}

// 2. Sử dụng trong code
public class BankAccount {
    private double balance = 100.0;

    public void withdraw(double amount) throws NotEnoughMoneyException {
        if (amount > balance) {
            // Ném lỗi tự tạo ra
            throw new NotEnoughMoneyException("Số dư không đủ để rút " + amount);
        }
        balance -= amount;
        System.out.println("Rút tiền thành công!");
    }

    public static void main(String[] args) {
        BankAccount acc = new BankAccount();
        try {
            acc.withdraw(500.0); // Cố tình rút quá số dư
        } catch (NotEnoughMoneyException e) {
            System.err.println("Giao dịch thất bại: " + e.getMessage());
        }
    }
}
```
## Tổng kết
 Exception Handling không chỉ là để sửa lỗi, mà là để kiểm soát rủi ro và giữ cho trải nghiệm người dùng không bị gián đoạn. Hãy ưu tiên dùng Try-with-resources và hạn chế Checked Exceptions không cần thiết.
 </div>
 <div class="btn-back-container">
    <a href="/NguyenDucQui_Blog/posts/" class="back-btn">Quay lại</a>
</div>