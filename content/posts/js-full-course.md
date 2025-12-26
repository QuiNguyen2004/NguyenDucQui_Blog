---
title: "JavaScript là gì? Tổng quan về ngôn ngữ lập trình JavaScript"
date: 2024-12-14
draft: false
summary: "Kiến thức về JavaScript"
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
### JavaScript là gì?

JavaScript là 1 trong 3 ngôn ngữ chính của lập trình web, và nó được dùng phổ biến trong suốt 20 năm qua. Từ thuở sơ khai, nó còn có tên là Mocha (năm 1995), sau đó được đổi thành Mona, Livescript, và cuối cùng là JavaScript như hiện nay.

Tính đến năm 2016, có đến 92% trang web hiện nay đang sử dụng JavaScript, và rất có thể bạn đã dùng qua rất nhiều trang web có sử dụng ngôn ngữ lập trình này.

![Ngôn ngữ JavaScript](/NguyenDucQui_Blog/javascript-la-gi-co-vai-tro-gi-cach-bat-javascript-tren.001.jpg)

### JavaScript hoạt động như thế nào?

JavaScript là ngôn ngữ diễn dịch. Điều này có nghĩa là trình duyệt sẽ đọc mã JavaScript và thực thi ngay lập tức, chứ không cần biên dịch trước thành một tệp riêng như một số ngôn ngữ khác.

Quy trình hoạt động cơ bản của JavaScript:
- Khi bạn truy cập một trang web, trình duyệt sẽ tải các tệp HTML, CSS và JavaScript.
- Trình duyệt tạo ra một mô hình gọi là DOM (Document Object Model) – mô tả cấu trúc của trang web dưới dạng cây.
- JavaScript sẽ tìm các phần tử trong DOM và thay đổi chúng dựa trên hành động của người dùng (như click chuột, cuộn chuột, gõ phím...).
- Sau đó, trình duyệt sẽ cập nhật hiển thị để phản ánh những thay đổi đó
### JavaScript có vai trò gì trong trình duyệt?
Thông thường, các trang web sẽ được nhúng trực tiếp JavaScript vào, hoặc sẽ sử dụng file .js để tham chiếu qua. Đây là ngôn ngữ phía máy khách, nghĩa là thay vì xử lý tập lệnh trên server của trang web, nó sẽ được tải về máy của khách truy cập và xử lý trên chính chiếc máy đó.

Cần chú ý, hiện nay có một số trình duyệt web phổ biến cho phép bạn bật/tắt JavaScript theo ý của bạn. Vậy nên, bạn cần biết những trang web mà bạn muốn truy cập sẽ bị ảnh hưởng như thế nào nếu như không có JavaScript hoạt động, từ đó sẽ quyết định có bật/tắt nó hay không.

![Ngôn ngữ JavaScript](/NguyenDucQui_Blog/vaitrojs.png)

### Ưu và nhược điểm của JavaScript
Khi so sánh với các đối thủ khác thì JavaScript có rất nhiều điểm mạnh có thể được kể đến dưới đây.

- Đối với lập trình viên: Đây là ngôn ngữ dễ học, dễ để phát hiện và sửa lỗi hơn. Thông qua JavaScript thì lập trình viên cũng có thể kiểm tra dữ liệu đầu vào, nhằm giảm bớt công việc kiểm tra thủ công. JavaScript cũng khá linh hoạt, và nó có thể được sử dụng ở nhiều nền tảng, trình duyệt, và không cần những công cụ quá phức tạp bởi chúng có thể được biên dịch bởi HTML từ trình duyệt web.

- Đối với khách truy cập: Ta có thể truy cập và tương tác với website hiệu quả hơn. Nhờ đặc tính gọn nhẹ mà chúng sẽ cho phép thực hiện các tác vụ trên trang web nhanh hơn.

![Ngôn ngữ JavaScript](/NguyenDucQui_Blog/javascript-la-gi-co-vai-tro-gi-cach-bat-javascript-tren.003.jpg)

Tuy nhiên, công cụ nào cũng sẽ điểm mạnh và điểm yếu. Dưới đây là một số điểm yếu mà bạn nên cân nhắc qua.

- Nó rất dễ bị khai thác, thế nên chúng thu hút rất nhiều hacker thực hiện tìm kiếm lỗi bảo mật để lợi dụng, từ đó sẽ chèn cắm các mã độc vào máy tính của người sử dụng.

- Việc linh hoạt hỗ trợ cho các thiết bị cũng có thể tạo ra trải nghiệm không đồng nhất trên các thiết bị này, và đôi khi một số trình duyệt sẽ không hỗ trợ sử dụng JavaScript.
</div>
<div class="btn-back-container">
    <a href="/NguyenDucQui_Blog/posts/" class="back-btn">Quay lại</a>
</div>