<p align="center"><img width="684" height="563" alt="image" src="https://github.com/user-attachments/assets/87ce6d54-9707-4590-b272-80998dad2a82" /></p>

## The HTTP Protocol (Giao thức truyền tải siêu văn bản)
**HTTP** (Hypertext transfer protocol) là giao thức giao tiếp hoạt động dựa trên mô hình **Client - Server**, tức là máy của người dùng (client) sẽ gửi yêu cầu (request) tới máy chủ (server), sau khi nhận được thông tin thì server mới trả về phản hồi (response) cho người dùng

Ví dụ, khi ta truy cập Facebook thì có thể hình dung mô hình hoạt động như sau:
1. Ta điền trên trình duyệt là `facebook.com`, khi này thì Client (Máy của ta) gửi yêu cầu đến Server (Máy chủ Facebook) để xin dữ liệu, tài nguyên,.. cần thiết
2. Sau khi Server tiếp nhận được yêu cầu, nó sẽ gửi về phản hồi những thông tin mà Client cần như là HTML/CSS, Hình ảnh,..
3. Khi Client nhận được các dữ liệu đó xong, nó có thể dùng để xử lí các việc cần thiết như HTML/CSS để hiển thị giao diện của Facebook

HTTP là giao thức không trạng thái (stateless protocol), tức là những request hay response được gửi độc lập với nhau. Mấy thằng gửi sau không biết bất cứ thông tin gì về mấy thằng gửi trước.

## HTTP Requests
Là thông tin được gửi từ Client đến Server để yêu cầu Server tìm hoặc xử lí thông tin mà Client mong muốn. Mọi thông điệp HTTP (bao gồm Request và Response) đều chứa một hoặc nhiều Header, mỗi Header nằm trên một dòng riêng biệt, sau phần Header sẽ là một dòng trống rồi mới đến phần Body (phần này thì có thể có hoặc không tuỳ method). 

Ví dụ:
```yaml
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

Dòng đầu tiên của mỗi HTTP Request được gọi là Request Line, luôn chứa 3 phần tách biệt bởi dấu cách bao gồm:
- **HTTP Method (Phương thức HTTP):** như ví dụ trên thì Method đang dùng là GET, chức năng của GET là thu thập tài nguyên từ phía Server và vì GET không có phần Body nên là sau phần Cookie (Header cuối) không có dấu cách rồi tới nội dung tiếp theo.
- **Request-URI (Đường dẫn tài nguyên):** xác định đường dẫn ở trong site mà Client muốn truy vấn tới, như ví dụ trên là request tới `/auth/488/YourDetails.ashx?uid=129 `
- **HTTP Version (Phiên bản HTTP):** thông tin về phiên bản mà Request đang dùng, như ví dụ là `HTTP/1.1`

> Phần 2 trong Request Line ở The Web Application Hacker's Handbook có bảo nó là The requested URL nhưng theo nhiều nguồn trên mạng hiện nay thì thuật ngữ đúng phải là Request-URI hay gọi đơn giản là đường dẫn. Vì URL thực chất phải bao gồm tên miền, giao thức, đường dẫn.. chứ không chỉ có mỗi cái `/auth/488/YourDetails.ashx?uid=129` là biết được URL.

```yaml
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

Kể từ dòng 2 của ví dụ trở đi, đó là các Header được gửi kèm trong Request, có thể phân tích một số cái tiêu biểu như:
- **Referer:** cho biết trang nào mà người dùng đang ở và gửi cái Request này. Như ví dụ thì Client đang ở `https://mdsec.net/auth/488/Home.ashx` rồi nhấn nút hay link gì đó để gửi Request này.
- **User-Agent:** cho biết thông tin về trình duyệt, hệ điều hành, phần mềm,.. của thằng gửi Request này. Như ví dụ trên thì cái dễ hiểu là người gửi đang dùng Windows, còn mấy thông tin khác thì thua.
- **Host:** cho biết tên miền (domain) mà Request đang hướng tới, phần này cần thiết vì nếu nhiều domain trỏ chung một Server đích thì cái phần Host này sẽ xác định được là nhảy vào domain nào.

## HTTP Responses
Là thông tin Server trả về Client sau khi nhận được Request từ Client. Cấu trúc của HTTP Response tương tự như Request chỉ khác là thay Request Line thành Status Line. Ví dụ một Response như dưới:

```yaml
HTTP/1.1 200 OK
Date: Tue, 19 Apr 2011 09:23:32 GMT
Server: Microsoft-IIS/6.0
X-Powered-By: ASP.NET
Set-Cookie: tracking=tI8rk7joMx44S2Uu85nSWc
X-AspNet-Version: 2.0.50727
Cache-Control: no-cache
Pragma: no-cache
Expires: Thu, 01 Jan 1970 00:00:00 GMT
Content-Type: text/html; charset=utf-8
Content-Length: 1067

<!DOCTYPE html PUBLIC “-//W3C//DTD XHTML 1.0 Transitional//EN” “http://
www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd”><html xmlns=”http://
www.w3.org/1999/xhtml” ><head><title>Your details</title>
...
```
Lần này ví dụ đã có thêm phần Body với dấu hiệu thấy rõ là sau một dấu cách lạc quẻ trong một chuỗi liên tiếp. 
Dòng đầu tiên của Response này là Status Line như có đề cập ở trên, nó cũng chia thành 3 phần bao gồm:
- **HTTP Version (Phiên bản HTTP)**
- **Status Code (Mã kết quả):** là một con số thể hiện trạng thái kết quả của lần Request trước đó, như ví dụ thì là `200` nghĩa là Request thành công và tài nguyên đã yêu cầu sẽ được gửi về
- **Reason Phrase:** giải thích thêm về trạng thái của Response bằng ngôn ngữ thay vì số nhu thằng Status Code, ở ví dụ thì là `OK`

Kể từ dòng thứ 2 trở đi thì là các Header, ta sẽ phân tích sau ở các phần sau. Và ở 4 dòng cuối của ví dụ ta có thể thấy đây là một Body được kèm theo trong Response, nó là một đoạn HTML, ta có thể hình dung như ví dụ truy cập Facebook ở đầu. Sau khi truy cập vào site thì Request để xin HTML/CSS để xử lí giao diện, sau khi Request được chấp nhận thì có Response trả về đoạn mã như trên để Client xử lí đồ hoạ.

## HTTP Methods (Phương thức HTTP)
Đây là các phương thức CHỈ ĐƯỢC SỬ DỤNG trong HTTP Request, hiện nay có tất cả là 9 phương thức phổ biến trong đó 2 cái `GET` và `POST` được sử dụng nhiều nhất.
- GET: được sử dụng để lấy tài nguyên theo URI đã cung cấp
- POST

## Tài liệu tham khảo
- The Web Application Hacker's Handbook
- [Tìm hiểu về HTTP (HyperText Transfer Protocol)](https://viblo.asia/p/tim-hieu-ve-http-hypertext-transfer-protocol-bJzKmgewl9N)
- [HTTP Request là gì? Các phương thức HTTP request](https://viblo.asia/p/http-request-la-gi-cac-phuong-thuc-http-request-6J3Zgy6A5mB)
- [Cùng tìm hiểu về HTTP request methods](https://viblo.asia/p/cung-tim-hieu-ve-http-request-methods-djeZ1xBoKWz)
