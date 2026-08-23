## Networking là gì?
Network đơn giản là các thứ được kết nối lại với nhau, ví dụ như một mạng lưới kết nối trao đổi thư giữa Alice/Bob/Jim như bên dưới, các mạng lưới điện được kết nối giữa các thành phố và nhà máy hay các cung đường giao thông được nối với nhau. Trong lĩnh vực CNTT, Networking (hay còn được gọi là mạng máy tính) cũng vận hành theo cách tương tự, nó kết nối các thiết bị lại với nhau tạo nên một mạng lưới truyền tải thông tin ở quy mô nhỏ hoặc bao quát toàn thế giới.

<p align="center"><img width="676" height="475" alt="image" src="https://github.com/user-attachments/assets/03695679-34f2-4707-a4b3-9fa971184f3b" /> </p>

## Internet là gì?

Internet là mạng của các mạng (network of networks), đúng như tên gọi là nó kết nối giữa các mạng nhỏ với nhau hình thành nên một mạng lưới truyền tải thông tin có quy mô toàn cầu. Những mạng nhỏ này ta định nghĩa là mạng riêng (private network), nó được dùng cho nhu cầu nội bộ như văn phòng, nhà riêng,.. Trong khi đó mạng kết nối những mạng riêng này lại với nhau được gọi là mạng chung (public network).

<p align="center"><img width="852" height="579" alt="image" src="https://github.com/user-attachments/assets/fd0f0284-3b5e-4355-b4b4-116b14af86c2" /> </p>

## Định danh thiết bị trong một mạng
Giống với con người thường có tên và dấu vân tay trong đó tên thì có thể thay đổi lúc nào cũng được nhưng vân tay thì chỉ có duy nhất, mỗi thiết bị cũng gắn với hai khái niệm là địa chỉ IP và địa chỉ MAC. Đó là những thứ sẽ giúp các thiết bị tìm được nhau và giao tiếp với nhau trong mạng.

### Địa chỉ IP

IP (Internet Protocol) là địa chỉ được dùng để định danh một thiết bị trong một mạng ở một khoảng thời gian xác định, có thể thay đổi giữa các thiết bị với nhau mà vẫn giữ được cùng địa chỉ IP (Ví dụ: trong nhà có Router WiFi ta dùng điện thoại kết nối vào thì nhận đc ip là `192.168.1.5`, sau đó máy ta sụp nguồn rồi mất kết nối WiFi, lúc đó ta dùng Laptop cũng kết nối vào WiFi thì cũng nhận được ip `192.168.1.5`)

<p align="center"><img width="1140" height="487" alt="image" src="https://github.com/user-attachments/assets/0b65b6b3-a080-4095-a6d1-c84795537a7d" /> </p>

Một địa chỉ IP được chia thành 4 octet (đơn vị dữ liệu có đúng 8 bit), giá trị của mỗi octet sẽ định hình nên địa chỉ IP của thiết bị trong mạng. Các con số trong octet được tính toán thông qua kĩ thuật gọi là IP addressing & subnetting ta sẽ bàn đến sau. Trong một mạng thì địa chỉ IP có thể chuyển từ thiết bị này sang thiết bị kia nhưng sẽ KHÔNG BAO GIỜ có một IP nằm trong nhiều (>1) thiết bị cùng lúc.

Địa chỉ IP sẽ tuân theo những tiêu chuẩn được gọi là các giao thức (Protocol). Các giao thức này đóng vai trò là xương sống của mạng lưới kết nối, nó giúp các thiết bị giao tiếp với nhau cùng một ngôn ngữ.

Như có đề cập trước đó thì có 2 loại mạng là chung và riêng, và tuỳ vào trường hợp thì một thiết bị có thể nằm ở cả mạng chung và mạng riêng. Lúc đó thì thiết bị sẽ có 2 địa chỉ IP được gọi là IP chung và IP riêng. IP riêng là IP để định danh thiết bị đó giữa các thiết bị với nhau trong mạng riêng. Ví dụ như hình bên dưới thì trong LAN (mạng nội bộ, mạng riêng) có 2 thiết bị có 2 IP riêng khác nhau

<p align="center"><img width="546" height="145" alt="image" src="https://github.com/user-attachments/assets/63549bbc-96c4-4b79-bdb7-abc50cb45c83" /> </p>

Còn IP chung là IP mà thiết bị đó kết nối từ mạng riêng vào mạng chung, nó sẽ được ISP (nhà cung cấp dịch vụ Internet) cung cấp thông qua Router. Như hình bên dưới thì sau khi 2 thiết bị ở trên kết nối ra Internet thì nó sẽ cùng một IP là `86.157.52.21`. 

<p align="center"><img width="383" height="118" alt="image" src="https://github.com/user-attachments/assets/ce44c6fc-1632-4504-887c-c49d0411ad0c" /></p>

**Tại sao như ta nói trước đó thì một IP không thể chứa nhiều thiết bị mà 2 thiết bị này đều có cùng IP chung?** Giải thích đơn giản là khi này cả 2 thiết bị đều kết nối vào Router, mà Router thì tính vào 1 thiết bị nên là khi này quy tắc đó vẫn thoả mãn. Và khi dữ liệu trả về LAN, để phân biệt được thiết bị nào sẽ nhận thì Router sẽ gán mỗi thiết bị một cổng (port) riêng biệt khi ra Internet. Cơ chế này được gọi là NAT (Network Address Translation), nhờ vậy nhiều thiết bị cùng IP chung ra Internet mà ko bị lẫn lộn dữ liệu.


Ngày nay, do nhu cầu sử dụng thiết bị của con người quá lớn nên dẫn đến việc IPv4 dần cạn kiệt. Và để giải quyết vấn đề đó thì các nhà nghiên cứu đã cho ra đời IPv6 với hiệu suất và số lượng vượt trội hơn. Như hình bên dưới là sự so sánh giữa hai loại IP. IPv6 đã đang dần được triển khai ngày nay và sẽ thay thế toàn bộ cản trở hiện tại trong tương lai.

<p align="center"> <img width="736" height="177" alt="image" src="https://github.com/user-attachments/assets/8b41d349-5c00-4702-86b2-74d3ccbf6497" /> </p>

### Địa chỉ MAC
Mỗi thiêt bị trong 1 mạng sẽ luôn có 1 giao diện mạng vật lý (Physical network interface), nó là 1 vi mạch nằm trong bo mạch chủ của thiết bị. Nó là thành phần linh kiện giúp định danh được thiết bị được sản xuất bởi nhà máy nào và nó được gọi là địa chỉ MAC. Địa chỉ MAC gồm 12 kí tự thuộc hệ thập lục phân (hệ cơ số gồm 16 kí tự trong máy tính) được chia thành từng cặp và phân tách bởi dấu 2 chấm. Ví dụ như ảnh dưới, 6 kí tự đầu tiên sẽ biểu diễn thông tin nhà máy sản xuất và 6 kí tự còn lại là các con số độc bản của thiết bị.

<img width="1140" height="669" alt="image" src="https://github.com/user-attachments/assets/5bd16e8e-c723-441b-bfb4-0eb5f998a9b4" />






