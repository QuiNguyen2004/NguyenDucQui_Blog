---
title: "Bài 1: Lập trình mạng cơ bản với Java Socket"
date: 2025-12-01
draft: false
tags: ["Java", "Network"]
---

## 1. Java Socket là gì?
Socket là điểm đầu cuối của liên kết truyền thông hai chiều giữa hai chương trình chạy trên mạng. Trong Java, gói `java.net` cung cấp các class để lập trình mạng.

* **Socket:** Dùng cho Client.
* **ServerSocket:** Dùng cho Server (để lắng nghe kết nối).

## 2. Code ví dụ: Client - Server đơn giản
Dưới đây là ví dụ tạo một Server lắng nghe và một Client gửi lời chào.

### Code Server (`Server.java`)
Server sẽ mở cổng 5000 và chờ kết nối.

```java
import java.io.*;
import java.net.*;

public class Server {
    public static void main(String[] args) {
        try {
            // 1. Mở cổng 5000
            ServerSocket serverSocket = new ServerSocket(5000);
            System.out.println("Server đang chạy và chờ kết nối...");

            // 2. Chấp nhận kết nối từ Client
            Socket socket = serverSocket.accept();
            System.out.println("Client đã kết nối!");

            // 3. Đọc dữ liệu từ Client gửi lên
            DataInputStream dis = new DataInputStream(socket.getInputStream());
            String message = dis.readUTF();
            System.out.println("Client nói: " + message);

            serverSocket.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```
### Code Client (`Client.java`)
Client kết nối tới Server (localhost) và gửi tin nhắn.

```java
import java.io.*;
import java.net.*;

public class Client {
    public static void main(String[] args) {
        try {
            // 1. Kết nối tới Server ở cổng 5000
            Socket socket = new Socket("localhost", 5000);

            // 2. Gửi dữ liệu đi
            DataOutputStream dos = new DataOutputStream(socket.getOutputStream());
            dos.writeUTF("Xin chào Server, mình là Client!");

            System.out.println("Đã gửi tin nhắn xong.");
            socket.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}