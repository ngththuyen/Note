<p align="center"><img width="684" height="563" alt="image" src="https://github.com/user-attachments/assets/87ce6d54-9707-4590-b272-80998dad2a82" /></p>

## The HTTP Protocol (Giao thức truyền tải siêu văn bản)
**HTTP** (Hypertext transfer protocol) là một giao thức giao tiếp cốt lõi để truy cập World Wide Web và nó từng được áp dụng trong tất cả các Website ngày xưa (còn nay chuyển sang HTTPS hết rồi). Nó hoạt động dựa trên mô hình **Client - Server**, tức là máy tính của người dùng (client) sẽ gửi yêu cầu (request) tới máy chủ (server), sau khi nhận được thông tin thì server mới trả về phản hồi (respond) cho người dùng. 

Ví dụ, khi ta truy cập Facebook thì có thể hình dung mô hình hoạt động như sau:
1. Ta điền trên trình duyệt là `facebook.com`, khi này thì Client (Máy của ta) gửi yêu cầu đến Server (Máy chủ Facebook) để xin dữ liệu, tài nguyên,.. cần thiết
2. Sau khi Server tiếp nhận được yêu cầu, nó sẽ gửi về phản hồi những thông tin mà Client cần như là HTML/CSS, Hình ảnh,..
3. Khi Client nhận được các dữ liệu đó xong, nó có thể dùng để xử lí các việc cần thiết như HTML/CSS để hiển thị giao diện của Facebook

HTTP là giao thức không trạng thai (stateless protocol), tức là những request hay respond được gửi đều độc lập với nhau. Mấy thằng gửi sau không biết bất cứ thông tin gì về mấy thằng gửi trước.

## HTTP Requests
Là thông tin được gửi từ Client đến Server để yêu cầu Server tìm hoặc xử lí thông tin, dữ liệu,.. mà Client mong muốn. Mọi thông điệp HTTP (bao gồm Request và Respond) đều chứa một hoặc nhiều header, mỗi header nằm trên một dòng riêng biệt, sau phần header sẽ là một dòng trống rồi mới đến phần body (có thể có hoặc không). 

Ví dụ:
```
GET /auth/488/YourDetails.ashx?uid=129 HTTP/1.1
Accept: application/x-ms-application, image/jpeg, application/xaml+xml,
image/gif, image/pjpeg, application/x-ms-xbap, application/x-shockwaveflash, */*
Referer: https://mdsec.net/auth/488/Home.ashx
Accept-Language: en-GB
User-Agent: Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1; WOW64;
Trident/4.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR
3.0.30729; .NET4.0C; InfoPath.3; .NET4.0E; FDM; .NET CLR 1.1.4322)
Accept-Encoding: gzip, deflate
Host: mdsec.net
Connection: Keep-Alive
Cookie: SessionId=5B70C71F3FD4968935CDB6682E545476
```

## Tài liệu tham khảo
- The Web Application Hacker's Handbook
- [Tìm hiểu về HTTP (HyperText Transfer Protocol)](https://viblo.asia/p/tim-hieu-ve-http-hypertext-transfer-protocol-bJzKmgewl9N)
- [HTTP Request là gì? Các phương thức HTTP request](https://viblo.asia/p/http-request-la-gi-cac-phuong-thuc-http-request-6J3Zgy6A5mB)

