---
title: "Java là gì? Tổng quan về ngôn ngữ lập trình Java"
date: 2024-12-14
draft: false
summary: "Toàn bộ kiến thức về Java"
ShowToc: true
TocOpen: true
hidemeta: false
---
**Java** là ngôn ngữ lập trình thuộc top phổ biến nhất thế giới, Java không chỉ phổ biến trong lập trình ứng dụng web và di động mà còn là xương sống của nhiều hệ thống lớn như các nền tảng giao dịch tài chính, hệ thống quản lý doanh nghiệp, và các ứng dụng nhúng. Vậy Java là gì? Java hoạt động ra sao và ứng dụng như thế nào? Cùng Duc Qui tìm hiểu tổng quan về ngôn ngữ lập trình Java này thông qua bài viết bên dưới nhé!
### Java là gì?


Java là một trong những ngôn ngữ lập trình hướng đối tượng. Ngôn ngữ Java được sử dụng phổ biến trong phát triển phần mềm, trang web, game hay ứng dụng trên các thiết bị di động.

Java được khởi đầu bởi James Gosling và bạn đồng nghiệp ở Sun MicroSystem năm 1991. Ban đầu Java được tạo ra nhằm mục đích viết phần mềm cho các sản phẩm gia dụng, và có tên là Oak. Java được chính thức phát hành năm 1994, đến năm 2010 được Oracle mua lại từ Sun MicroSystem.

### Đặc điểm của ngôn ngữ lập trình Java là gì?

![ảnh đặt điểm java](/NguyenDucQui_Blog/dac-diem-cua-java.png)

#### Tương tự C++, hướng đối tượng hoàn toàn

Trong quá trình tạo ra một ngôn ngữ mới phục vụ cho mục đích chạy được trên nhiều nền tảng, các kỹ sư của Sun MicroSystem muốn tạo ra một ngôn ngữ dễ học và quen thuộc với đa số người lập trình. Vì vậy họ đã sử dụng lại các cú pháp của C và C++.

Tuy nhiên, trong Java thao tác với con trỏ bị lược bỏ nhằm đảo bảo tính an toàn và dễ sử dụng hơn. Các thao tác overload, goto hay các cấu trúc như struct và union cũng được loại bỏ khỏi Java.

#### Độc lập phần cứng và hệ điều hành

Một chương trình viết bằng ngôn ngữ Java có thể chạy tốt ở nhiều môi trường khác nhau. Gọi là khả năng “cross-platform”. Khả năng độc lập phần cứng và hệ điều hành được thể hiện ở 2 cấp độ là cấp độ mã nguồn và cấp độ nhị phân.

Ở cấp độ mã nguồn: Kiểu dữ liệu trong Java nhất quán cho tất cả các hệ điều hành và phần cứng khác nhau. Java có riêng một bộ thư viện để hỗ trợ vấn đề này. Chương trình viết bằng ngôn ngữ Java có thể biên dịch trên nhiều loại máy khác nhau mà không gặp lỗi.

Ở cấp độ nhị phân: Một mã biên dịch có thể chạy trên nhiều nền tảng khác nhau mà không cần dịch lại mã nguồn. Tuy nhiên cần có Java Virtual Machine để thông dịch đoạn mã này.

#### Ngôn ngữ thông dịch

Ngôn ngữ lập trình thường được chia ra làm 2 loại (tùy theo các hiện thực hóa ngôn ngữ đó) là ngôn ngữ thông dịch và ngôn ngữ biên dịch.

Thông dịch (Interpreter) : Nó dịch từng lệnh rồi chạy từng lệnh, lần sau muốn chạy lại thì phải dịch lại.
Biên dịch (Compiler): Code sau khi được biên dịch sẽ tạo ra 1 file thường là .exe, và file .exe này có thể đem sử dụng lại không cần biên dịch nữa.
Ngôn ngữ lập trình Java thuộc loại ngôn ngữ thông dịch. Chính xác hơn, Java là loại ngôn ngữ vừa biên dịch vừa thông dịch. Cụ thể như sau

Khi viết mã, hệ thống tạo ra một tệp .java. Khi biên dịch mã nguồn của chương trình sẽ được biên dịch ra mã byte code. Máy ảo Java (Java Virtual Machine) sẽ thông dịch mã byte code này thành machine code  (hay native code) khi nhận được yêu cầu chạy chương trình.

![Java-compiler](/NguyenDucQui_Blog/java-compiler.png)

##### Ưu điểm
 Phương pháp này giúp các đoạn mã viết bằng Java có thể chạy được trên nhiều nền tảng khác nhau. Với điều kiện là JVM có hỗ trợ chạy trên nền tảng này.

##### Nhược điểm
 Cũng như các ngôn ngữ thông dịch khác, quá trình chạy các đoạn mã Java là chậm hơn các ngôn ngữ biên dịch khác (tuy nhiên vẫn ở trong một mức chấp nhận được)

---

### Đa luồng

Java hỗ trợ lập trình đa tiến trình (multithread) để thực thi các công việc đồng thời. Đồng thời cũng cung cấp giải pháp đồng bộ giữa các tiến trình (giải pháp sử dụng priority…).


![Ảnh đa luồng Java](/NguyenDucQui_Blog/daluongjava.png)

### Hướng dẫn tải và cài đặt Java trên Windows

Việc tải về và cài đặt Java trên máy tính Windows của bạn không hề phức tạp nếu bạn làm theo từng bước hướng dẫn của chúng tôi. Quá trình này khá giống nhau trên tất cả các phiên bản Windows, ở đây TopDev sẽ thực hiện trên Windows 11.
👉 **Tải xuống Java chính chủ tại đây:** [Oracle Java Download](https://www.oracle.com/javadownload/)

#### Bước 1: Tải xuống Java về máy tính

Mở trang tải xuống Java cho Windows và nhấp vào liên kết tải xuống trình cài đặt x64.

Chọn phiên bản JDK mới nhất. Trong ví dụ này, phiên bản mới nhất có sẵn là JDK 22 .
Truy cập vào tab Windows .
Nhấp vào liên kết tải xuống x64 Installer

![Hướng dẫn tải Java](/NguyenDucQui_Blog/tai-java.png)

#### Bước 2: Setup Java trên hệ thống Windows

Nhấp đúp vào tệp Java đã tải xuống để bắt đầu cài đặt.
Khi màn hình chào mừng của trình hướng dẫn cài đặt xuất hiện, hãy chọn Next để tiếp tục.

![Hướng dẫn tải Java](/NguyenDucQui_Blog/cai-dat-java-1.png)

Quá trình cài đặt hoàn tất khi thông báo Successfully Installed xuất hiện. Nhấp vào Close để thoát khỏi trình hướng dẫn.

Tới đây bạn đã cài đặt thành công JDK 22 trên hệ thống Windows của mình. Để cho phép biên dịch chương trình từ bất kỳ thư mục nào, bạn phải thiết lập biến môi trường Java.

#### Bước 3: Thiết lập biến môi trường trong Java

Thực hiện theo các bước trong phần bên dưới để cấu hình biến môi trường Java trong Windows.

##### + Thêm Java vào Biến Hệ thống
Bước này đảm bảo rằng Java có thể truy cập được từ dòng lệnh trong bất kỳ thư mục nào.

1. Mở menu Start và tìm kiếm “environment variables”

2. Chọn Edit the system environment variables.

![Thiết lap moi truong 1](/NguyenDucQui_Blog/thiet-lap-bien-moi-truong-java-1-1.png)

3. Chọn Advanced.

4. Nhấp vào Environment variables.

![Thiết lap moi truong 2](/NguyenDucQui_Blog/cach-thiet-lap-bien-moi-truong-java-2.png)

5. Chọn biến Path trong danh mục System variables và nhấp vào Edit.

![Thiết lap moi truong 3](/NguyenDucQui_Blog/cach-thiet-lap-bien-moi-truong-java-3.png)

6. Nhấp vào New.

7. Nhập đường dẫn đến thư mục Java bin..

8. Nhấp vào OK để lưu các thay đổi và thoát khỏi cửa sổ chỉnh sửa biến.

![Thiết lap moi truong 4](/NguyenDucQui_Blog/cach-thiet-lap-bien-moi-truong-java-4.png)

##### + Thêm biến JAVA_HOME

1. Nhấp vào New trong danh mục System variables để tạo biến mới.

![Thiết lap moi truong 5](/NguyenDucQui_Blog/cach-thiet-lap-bien-moi-truong-java-5.png)

2. Đặt tên biến là JAVA_HOME.

3. Nhập đường dẫn đến thư mục Java JDK của bạn vào trường giá trị biến.

4. Nhấp vào OK.

![Thiết lap moi truong 6](/NguyenDucQui_Blog/cach-thiet-lap-bien-moi-truong-java-6.png)

Bây giờ bạn đã tạo thành công biến môi trường Java trên thiết bị Windows 11 của mình.