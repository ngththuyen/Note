## Networking là gì?
Network đơn giản là các thứ được kết nối lại với nhau, ví dụ như một mạng lưới kết nối trao đổi thư giữa Alice/Bob/Jim như bên dưới, các mạng lưới điện được kết nối giữa các thành phố và nhà máy hay các cung đường giao thông được nối với nhau. Trong lĩnh vực CNTT, Networking (hay còn được gọi là mạng máy tính) cũng vận hành theo cách tương tự, nó kết nối các thiết bị lại với nhau tạo nên một mạng lưới truyền tải thông tin ở quy mô nhỏ hoặc bao quát toàn thế giới.

<p align="center"><img width="676" height="475" alt="image" src="https://github.com/user-attachments/assets/03695679-34f2-4707-a4b3-9fa971184f3b" /> </p>

## Internet là gì?

Internet là mạng của các mạng (network of networks), đúng như tên gọi là nó kết nối giữa các mạng nhỏ với nhau hình thành nên một mạng lưới truyền tải thông tin có quy mô toàn cầu. Những mạng nhỏ này ta định nghĩa là mạng riêng (private network), nó được dùng cho nhu cầu nội bộ như văn phòng, nhà riêng,.. Trong khi đó mạng kết nối những mạng riêng này lại với nhau được gọi là mạng chung (public network).

<p align="center"><img width="852" height="579" alt="image" src="https://github.com/user-attachments/assets/fd0f0284-3b5e-4355-b4b4-116b14af86c2" /> </p>

## Định danh thiết bị trong một mạng
Giống với con người thường có tên và dấu vân tay trong đó tên thì có thể thay đổi lúc nào cũng được nhưng vân tay thì chỉ có duy nhất, mỗi thiết bị cũng gắn với hai khái niệm là địa chỉ IP và địa chỉ MAC. Đó là những thứ sẽ giúp các thiết bị tìm được nhau và giao tiếp với nhau trong mạng.

### Địa chỉ IP

IP (Internet Protocol) là địa chỉ được dùng để định danh một thiết bị trong một mạng ở một khoảng thời gian xác định, có thể thay đổi giữa các thiết bị với nhau mà vẫn giữ được cùng địa chỉ IP (Ví dụ: trong nhà có Router WiFi lúc sáng ta dùng điện thoại kết nối vào thì nhận đc ip là `192.168.1.5`, sau đó máy ta sụp nguồn rồi mất kết nối WiFi, lúc đó ta dùng Laptop cũng kết nối vào WiFi thì cũng nhận được ip `192.168.1.5`)

<p align="center"><img width="1140" height="487" alt="image" src="https://github.com/user-attachments/assets/0b65b6b3-a080-4095-a6d1-c84795537a7d" /> </p>

Một địa chỉ IP được chia thành 4 octet (đơn vị dữ liệu có đúng 8 bit), giá trị của mỗi octet sẽ định hình nên địa chỉ IP của thiết bị trong mạng. Các con số trong octet được tính toán thông qua kĩ thuật gọi là IP addressing & subnetting ta sẽ bàn đến sau. Trong một mạng thì địa chỉ IP có thể chuyển từ thiết bị này sang thiết bị kia nhưng sẽ KHÔNG BAO GIỜ có một IP nằm trong nhiều (>1) thiết bị cùng lúc.






