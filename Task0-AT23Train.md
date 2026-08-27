<p align="center"><img width="684" height="563" alt="image" src="https://github.com/user-attachments/assets/87ce6d54-9707-4590-b272-80998dad2a82" /></p>

## The HTTP Protocol (Giao thức truyền tải siêu văn bản)
**HTTP** (Hypertext transfer protocol) là giao thức tiêu chuẩn cho World Wide Web. Giống như một ngôn ngữ chung, HTTP cho phép các máy tính giao tiếp được với nhau và trao đổi thông tin. Nó hoạt động dựa trên mô hình **Client - Server**, tức là máy của người dùng (client) sẽ gửi yêu cầu (request) tới máy chủ (server), sau khi nhận được thông tin thì server mới trả về phản hồi (response) cho người dùng

Ví dụ, khi ta truy cập Facebook thì có thể hình dung mô hình hoạt động như sau:
1. Ta điền trên trình duyệt là `facebook.com`, khi này thì Client (Máy của ta) gửi yêu cầu đến Server (Máy chủ Facebook) để xin dữ liệu, tài nguyên,.. cần thiết
2. Sau khi Server tiếp nhận được yêu cầu, nó sẽ gửi về phản hồi những thông tin mà Client cần như là HTML/CSS, Hình ảnh,..
3. Khi Client nhận được các dữ liệu đó xong, nó có thể dùng để xử lí các việc cần thiết như HTML/CSS để hiển thị giao diện của Facebook

HTTP là giao thức không trạng thái (stateless protocol), tức là những request hay response được gửi độc lập với nhau. Mấy thằng gửi sau không biết bất cứ thông tin gì về mấy thằng gửi trước.

## HTTP Requests
Là yêu cầu được gửi từ Client đến Server để yêu cầu Server tìm hoặc xử lí thông tin mà Client mong muốn. Mọi thông điệp HTTP (bao gồm Request và Response) đều chứa một hoặc nhiều Header, mỗi Header nằm trên một dòng riêng biệt, sau phần Header sẽ là một dòng trống rồi mới đến phần Body (phần này thì có thể có hoặc không tuỳ method). 

Ví dụ:
```http
GET /auth/488/YourDetails.ashx?uid=129 HTTP/1.1
Accept: application/x-ms-application, image/jpeg, application/xaml+xml, image/gif, image/pjpeg, application/x-ms-xbap, application/x-shockwaveflash, */*
Referer: https://mdsec.net/auth/488/Home.ashx
Accept-Language: en-GB
User-Agent: Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1; WOW64; Trident/4.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; .NET4.0C; InfoPath.3; .NET4.0E; FDM; .NET CLR 1.1.4322)
Accept-Encoding: gzip, deflate
Host: mdsec.net
Connection: Keep-Alive
Cookie: SessionId=5B70C71F3FD4968935CDB6682E545476
```

Dòng đầu tiên của mỗi HTTP Request được gọi là Request Line, luôn chứa 3 phần tách biệt bởi dấu cách bao gồm:
- **HTTP Method (Phương thức HTTP):** như ví dụ trên thì Method đang dùng là GET, chức năng của GET là thu thập tài nguyên từ phía Server và vì GET không có phần Body nên là sau phần Cookie (Header cuối) không có dấu cách rồi tới nội dung tiếp theo.
- **Request-URI (Đường dẫn tài nguyên):** xác định đường dẫn ở trong site mà Client muốn truy vấn tới, như ví dụ trên là request tới `/auth/488/YourDetails.ashx?uid=129 `
- **HTTP Version (Phiên bản HTTP):** thông tin về phiên bản mà Request đang dùng, như ví dụ là `HTTP/1.1`

```http
Accept: application/x-ms-application, image/jpeg, application/xaml+xml, image/gif, image/pjpeg, application/x-ms-xbap, application/x-shockwaveflash, */*
Referer: https://mdsec.net/auth/488/Home.ashx
Accept-Language: en-GB
User-Agent: Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1; WOW64; Trident/4.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; .NET4.0C; InfoPath.3; .NET4.0E; FDM; .NET CLR 1.1.4322)
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

```http
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
- **Status Code (Mã trạng thái):** là một con số thể hiện trạng thái kết quả của lần Request trước đó, như ví dụ thì là `200` nghĩa là Request thành công và tài nguyên đã yêu cầu sẽ được gửi về
- **Reason Phrase:** giải thích thêm về trạng thái của Response bằng ngôn ngữ thay vì số nhu thằng Status Code, ở ví dụ thì là `OK`

Kể từ dòng thứ 2 trở đi thì là các Header, ta sẽ phân tích sau ở các phần sau. Và ở 4 dòng cuối của ví dụ ta có thể thấy đây là một Body được kèm theo trong Response, nó là một đoạn HTML, ta có thể hình dung như ví dụ truy cập Facebook ở đầu. Sau khi truy cập vào site thì Request để xin HTML/CSS để xử lí giao diện, sau khi Request được chấp nhận thì có Response trả về đoạn mã như trên để Client xử lí đồ hoạ.

## HTTP Methods (Phương thức HTTP)
Đây là các phương thức CHỈ ĐƯỢC SỬ DỤNG trong HTTP Request, hiện nay có tất cả là 9 phương thức phổ biến trong đó 2 cái `GET` và `POST` được sử dụng nhiều nhất.
- **GET:** được sử dụng để lấy tài nguyên theo URI đã cung cấp, nó có thể gửi các tham số đến nguồn tài nguyên được truy vấn thông qua URL vì thế nên thường không được sử dụng vào các thao tác thu thập thông tin nhạy cảm như Login. Một ví dụ cho thấy nó có thể lộ dữ liệu trên URL là: `example.com/login.php?user=ngththuyen&password=123`
- **POST:** được sử dụng để thực hiện các hành động như là gửi thông tin hay tạo tài nguyên mới lên máy chủ, điểm khác biệt so với GET là POST sẽ cho phép đặt các tham số của Request trên cả URL và Body. Việc này giúp cho POST xử lí dữ liệu nhạy cảm tốt hơn khi các thông tin như password có thể đặt tại phần Body của Request còn các thông tin ngoài lề có thể đặt ở URL.
- **HEAD:** hoạt động y hệt GET nhưng Response trả về sẽ không có Body, chỉ có Header. Và vì nó không lấy cả Body nên phương thức này thường được ứng dụng để kiểm tra trang tài nguyên đích có tồn tại hay không trước khi dùng GET vào để lấy thông tin thay vì dùng GET ngay từ đầu sẽ tốn thời gian tải tài nguyên.
- **TRACE:** được sử dụng để kiểm tra, check bệnh bằng việc gửi Request từ Client và yêu cầu Server trả lại nguyên văn Request đó. Nếu trong quá trình gửi, Request bị thay đổi ở phần nào đó khiến Server trả về nội dung khác với Request ban đầu thì có thể phán là có bệnh.
- **OPTIONS:** được dùng để hỏi Server xem cho phép những phương thức HTTP Request nào. Server thường trả về Header Allow những Method được phép như `Allow: GET, POST, OPTIONS`
- **PUT:** được dùng để ghi đè, tạo mới tài nguyên tại đường dẫn cụ thể trong Server
- **PATCH:** được dùng để cập nhật một phần tài nguyên đã có sẵn trên Server
- **DELETE:** được dùng xoá tài nguyên trên Server
- **CONNECT:** được dùng để thiết lập một kênh kết nối giữa Client và Server thông qua một thằng trung gian

## HTTP Headers 
HTTP ngày nay hỗ trợ số lượng lớn Header, có cái dành cho cả Request và Response, có cái chỉ dành cho 1 trong 2. Dưới đây là những Header thông dụng được tách ra 3 nhóm gồm General, Request và Response:

### General Headers
- **Connection:** kết nối mạng giữa Client và Server có được mở tiếp không hay là đóng lại. Trường thông tin này có thể nhận 1 trong 2 giá trị là `keep-alive` và `close` tương ứng tiếp tục và đóng kết nối.
- **Content-Encoding:** loại mã hoá nào được sử dụng cho Body để tăng tốc độ truyền tải, loại phổ biến ta thường thấy là `gzip`
- **Content-Length:** chỉ độ dài của phần Body bằng đơn vị Byte (Header này trong Medhod HEAD sẽ chỉ độ dài của Body khi sử dụng GET trong lần tới chứ HEAD response không có Body)
- **Content-Type:** chỉ loại nội dung được trình bày trong phần Body, ví dụ như `text/html` là nói về Body đang chứa mã HTML
- **Transfer-Encoding:** chỉ loại mã hoá nào được sử dụng cho toàn bộ truy vấn đó, khác với Content-Encoding chỉ encode Body thôi thì cái này encode hết
### Request Headers
- **Accept:** chỉ định dạng dữ liệu mà Client muốn nhận từ Server ví dụ như `application/json` là muốn nhận Response có định dạng json
- **User-Agent:** chỉ thông tin về thiết bị, trình duyệt hay ứng dụng mà Client đang dùng, việc này giúp Server có thể trả về những thông tin tương thích với Client
- **Authorization:** chỉ thông tin xác thực để gửi tới Server khi Request vào tài nguyên cần quyền truy cập
- **Cookie:** chỉ thông tin Cookie mà Client lưu trước đó được gửi cho Server, giúp xác định session và cá nhân hoá trải nghiệm
### Response Headers
- **Server:** thông tin về phần mềm mà Web Server đang vận hành, ví dụ `Server: Apache/2.4.10 (Unix)`
- **Cache-Control:** điều khiển việc lưu bộ nhớ đệm (cache) ở phía trình duyệt hoặc các cache trung gian
- **Set-Cookie:** chỉ định Cookie mà Client sẽ Request trong các lần tiếp theo
- **Expires:** nói cho trình duyệt biết nội dung trong phần Body sẽ có thời hạn là bao lâu
- **WWW-Authenticate:** báo cho Client biết phương thức xác thực nào cần dùng để truy cập vào tài nguyên được bảo vệ

## Cookies
Cookie HTTP là phần dữ liệu nhỏ mà Server gửi tới Client, sau đó Browser của Client sẽ lưu trữ Cookie đó và gửi lại cho Server đó ở các Request sau này. Tại sao phải cần Cookie? Như ta đã biết thì HTTP là một stateless protocol tức các truy vấn đều độc lập, chả liên quan gì đến nhau và điều đó khiến cho Server không xác định được các request có phải đến từ cùng 1 Client hay không. Và do đó, Cookie ra đời để xử lí vấn đề này, những công dụng của Cookie ta có thể dễ thấy như việc truy cập vào Facebook trong 1 máy lần đầu thì ta thấy nó bắt đăng nhập nhưng ở một số lần sau thì không còn yêu cầu đăng nhập nữa vì Server đã biết mình là ai thông qua Cookie.

Bên cạnh việc lưu lại phiên đăng nhập, Cookie còn lưu một số thông tin cơ bản khác của Client như giỏ hàng, ngôn ngữ, vị trí,.. tuỳ Web. Cookie còn hỗ trợ các doanh nghiệp theo dõi hành vi người dùng để thực hiện chiến dịch quảng cáo, ta có thể hình dung qua việc ta search 1 sản phẩm trên nền tảng A thì tự nhiên khi sử dụng nền tảng B nó xuất hiện loạt quảng cáo về sản phẩm đó.

Ví dụ một quy trình Cookie được gửi và lưu như sau:
1. Client gửi HTTP Request đến với Server, sau khi nhận được yêu cầu và xác thực xong thì Server trả về HTTP Response cho Client có một hoặc nhiều hoặc không có Header `Set-Cookie` để đặt Cookie cho Browser Client đó
```http
HTTP/2.0 200 OK
Content-Type: text/html
Set-Cookie: yummy_cookie=chocolate
Set-Cookie: tasty_cookie=strawberry

[page content]
```
2. Sau khi nhận được Cookie từ Response, Client kể từ các lần HTTP Request sau sẽ sử dụng Header `Cookie` chứa giá trị Cookie đã được set cho tới khi hết hạn hoặc là được set bằng giá trị khác
```http
GET /sample_page.html HTTP/2.0
Host: www.example.org
Cookie: yummy_cookie=chocolate; tasty_cookie=strawberry
```

Mỗi Cookie được set thì thường có thời hạn sử dụng, như ở ví dụ trên thì không sử dụng thẻ `Expires` hay `Max-Age` thì Cookie sẽ chỉ tồn tại trong Session (dữ liệu tạm thời của người dùng được lưu ở phía máy chủ) đó, tức là sau khi Client đóng Tab Website thì Cookie bị hết hạn. 

## Status Code
Mỗi HTTP Response luôn chứa một Status Code (Mã trạng thái) ở dòng đầu để xác định trạng thái kết quả của Request mà Client gửi trước đó. Mã này có tác dụng xác định được Request trước đó gửi có thành công hay không, nếu thất bại thì lỗi do gì. Status Code được chia thành 5 nhóm dựa vào con số đầu của mỗi mã:
- **`1xx`** - Mã chứa thông tin, đơn giản là chỉ báo Client là Server đã nhận được Request
- **`2xx`** - Mã báo Request trước đó được gửi tới Server đã thành công
- **`3xx`** - Mã báo Client đã được chuyển tiếp sang một nguồn tài nguyên khác
- **`4xx`** - Mã báo có lỗi ở phía Client khi gửi Request
- **`5xx`** - Mã báo có lỗi ở phía Server khi xử lí Request được gửi

Có rất nhiều mã cụ thể tương ứng từng công dụng khác nhau, đây là một số mã ví dụ nổi tiếng mà chúng ta hay gặp:
- `100 Continue` cho biết một phần Request trước đó gửi tới Server đã được tiếp nhận và nó yêu cầu gửi tới tiếp những nội dung tiếp theo (Ví dụ Request có chứa Header và Body nhưng mới gửi tới Header thôi thì nó báo trước để biết là Header đã tới còn Body chưa có)
- `200 OK` cho biết Request đã được tiếp nhận và xử lí thành công
- `201 Created` cho biết Request đã được nhận và thực hiện thành công phương thức PUT
- `301 Moved Permanently` cho biết tài nguyên của Request hiện tại và các Request sau đã được chuyển sang URI mới
- `302 Found` cho biết URI của tài nguyên được Request đã tạm thời bị thay đổi, có thể có một số thay đổi cho URI trong tương lai nên yêu cầu Client dùng URI cũ trong các lần Request tiếp theo
- `400 Bad Request` cho biết Server không thể xử lí Request của Client vì nó chứa những nội dung không hợp lệ như là lỗi cú pháp, định dạng,..
- `401 Unauthorized` cho biết Client cần phải xác thực để được Server xử lí Request
- `403 Forbidden` cho biết không ai được truy cập vào tài nguyên này, bất kể đã xác thực
- `404 Not Found` cho biết tài nguyên Request tới không tồn tại
- `405 Method Not Allowed` cho biết Method (phương thức) được sử dụng trong Request ko được hỗ trợ
- `413 Request Entity Too Large/Content Too Large` dữ liệu trong Request quá giới hạn cho phép của Server
- `414 Request URI Too Long` URI quá dài để Server xử lí
- `500 Internal Server Error` thông báo chung chung, báo Server bị lỗi gì đó
- `503 Service Unavailable` Server đang không có sẵn, có thể bị quá tải hoặc dừng để bảo trì

## HTTPS (Hypertext Transfer Protocol Secure)
Là HTTP nhưng có thêm "Secure", tức là bảo mật hơn. Nó mã hoá thông tin bằng chứng chỉ SSL/TSL rồi mới cho phép trao đổi giữa Client và Server. Đây là giao thức được sử dụng rộng rãi hiện nay nhờ độ bảo mật vượt trội giúp các thao tác giữa người dùng và máy chủ an toàn hơn.

## HTTP Proxies
Là Server trung gian đứng giữa Client Browser và Web Server, khi một Browser có setup Proxy thì mọi Request được Client gửi đều gửi tới Proxy rồi Proxy gửi qua Server và Server trả Response về cũng trả cho Proxy rồi Proxy gửi lại Client. Việc này giúp Client có thể giấu IP gốc, lọc nội dung hay là bảo mật khi cần quản lí một số tài nguyên nhạy cảm.

## HTTP Authentication
Là một cơ chế bảo mật kiểm tra xem người dùng có đủ điều kiện truy cập hay không

## Tài liệu tham khảo
- The Web Application Hacker's Handbook
- [Tìm hiểu về HTTP (HyperText Transfer Protocol)](https://viblo.asia/p/tim-hieu-ve-http-hypertext-transfer-protocol-bJzKmgewl9N)
- [HTTP Request là gì? Các phương thức HTTP request](https://viblo.asia/p/http-request-la-gi-cac-phuong-thuc-http-request-6J3Zgy6A5mB)
- [Cùng tìm hiểu về HTTP request methods](https://viblo.asia/p/cung-tim-hieu-ve-http-request-methods-djeZ1xBoKWz)
- [HTTP Header là gì? Ví dụ về các trường phổ biến trong Request Header](https://vietnix.vn/http-header-la-gi)
- [Tìm hiểu về Cookies](https://viblo.asia/p/tim-hieu-ve-cookies-bXP4W5YKL7G)
- [Session và Cookie](https://viblo.asia/p/tim-hieu-ve-cookies-bXP4W5YKL7G)
- [Cookies là gì? Công dụng của Cookies trên trình duyệt? Cách xóa và bật quản lý Cookies trên Chrome](https://www.dienmayxanh.com/kinh-nghiem-hay/cookies-la-gi-cach-xoa-va-bat-quan-ly-cookies-tren-1133890)
- [Using HTTP cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Cookies)
- [HTTP Status code là gì? Các loại http status code](https://viblo.asia/p/http-status-code-la-gi-cac-loai-http-status-code-gDVK2dOXlLj)
- [HTTP response status codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status)
- [HTTPS là gì? HTTP và HTTPS khác nhau ở điểm nào?](https://viettelidc.com.vn/tin-tuc/https-la-gi)
- [HTTP Authentication là gì? Cách thức hoạt động](https://bkhost.vn/blog/http-authentication)
