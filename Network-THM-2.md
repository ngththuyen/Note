## Cấu trúc mạng cục bộ (LAN Topologies)
Qua nhiều năm, đã có rất nhiều cấu trúc mạng được nghiên cứu và ra đời. Trong lĩnh vực mạng máy tính, thuật ngữ "Topology" có nghĩa là thiết kế và hình dạng của mạng LAN ta nhắc đến. Dưới đây là những cấu trúc phổ biến và ưu nhược của chúng.

### Mạng hình sao (Star Topology)
Nguyên lí cấu trúc này là mọi thiết bị trong mạng đều độc lập kết nối với một thiết bị mạng trung tâm như Hub hoặc Switch. Đây là cấu trúc phổ biến nhất hiện nay vì độ hiệu quả và khả năng mở rộng của nó. Mọi thông tin mà thiết bị này muốn gửi sang cho thiết bị khác trong cùng mạng đều được thực hiện qua thiết bị mạng trung tâm. 

Và vì để triển khai cấu trúc này cần nhiều thiết bị chuyên dụng cũng như dây cáp hơn nên nó đắt hơn so với bất kì cấu trúc mạng khác. Tuy đắt nhưng cũng không phải là vô dụng, nó cũng cung cấp những ưu điểm vượt trội điển hình như khả năng mở rộng, khi nhu cầu thiết bị sử dụng mạng tăng thì việc thêm thiết bị vào vô cùng dễ dàng.

Tuy nhiên, mạng càng được mở rộng thì việc bảo trì càng phải được thực hiện thường xuyên để đảm bảo vận hành ổn định cũng như là việc quá phụ thuộc vào thiết bị trung tâm sẽ khiến các thiết bị kết nối bị ảnh hưởng khi thiết bị trung tâm có vấn đề. May thay, ngày nay các thiết bị trung tâm được thiết kế khá bền và hạn chế rất nhiều lỗi vận hành.

<p align="center"><img width="560" height="475" alt="image" src="https://github.com/user-attachments/assets/0963b86b-7076-40eb-b90d-3cc9b2686718" />
</p>

### Mạng hình bus (Bus Topology)
Kiểu cấu trúc này phụ thuộc vào một trục kết nối chính gọi là cáp trục chính (backbone cable). Có thể hình dung cấu trúc này như một nhánh cây, trong đó có các chiếc lá (thiết bị) mọc ra từ nhánh cây đó.

Và vì tất cả thiết bị đều cùng kết nối vào một cáp chính nên rất dễ xảy ra tình trạng tắc nghẽn nếu nhiều thiết bị đồng thời sử dụng. Việc tắc nghẽn này cũng rất khó xác định được thiết bị nào gặp vấn đề vì dữ liệu của tất cả đều dùng chung một cáp chính. Bên cạnh đó khả năng xử lí khi xảy ra sự cố cũng rất hạn chế, khi cáp bị đứt ở đâu đó thì cả mạng tê liệt.

Tuy nhiên, cấu trúc này lại là một trong những kiểu rất dễ triển khai và tốn rất ít chi phí so với các kiểu khác.

<p align="center"><img width="560" height="475" alt="image" src="https://github.com/user-attachments/assets/f43660aa-252c-4f4a-9794-068fa7ea4474" /> </p>

### Mạng hình vòng (Ring Topology)
Là cấu trúc kết nối các thiết bị như máy tính lại với nhau tạo thành một vòng tròn khép kín. Và vì kết nối thẳng giữa các thiết bị nên không cần thiết bị chuyên dụng như kiểu sao và hạn chế được lượng dây cáp.

Cấu trúc mạng này hoạt động bằng cách gửi dữ liệu chạy xuyên qua các thiết bị cho tới khi tìm được tới đích. Thú vị là một thiết bị trong mạng này sẽ chỉ gửi dữ liệu nó nhận được từ thiết bị khác sang thiết bị tiếp theo nếu như chính nó không có dữ liệu nào cần phải gửi. Còn nếu nó có dữ liệu cần gửi thì nó sẽ gửi dữ liệu của nó trước rồi mới gửi dữ liệu nó nhận được sau.

Và bởi vì cấu trúc mạng này chỉ có một chiều gửi nên lỗi phát sinh rất dễ được phát hiện và xử lí. Tuy nhiên đây là con dao hai lưỡi vì việc truyền tải dữ liệu qua nhiều thiết bị khác mới tới thiết bị đích không phải là phương án hiệu quả trong một mạng.

Cuối cùng, vì lượng dữ liệu không tập trung đông đúc vào một nơi như kiểu bus nên việc tắt nghẽn rất khó xảy ra. Nhưng cấu trúc mạng này rất dễ gặp sự cố nếu như một dây cáp hay thiết bị bị hỏng, cả mạng sẽ không thể hoạt động.

<p align="center"><img width="560" height="475" alt="image" src="https://github.com/user-attachments/assets/f8c21efa-074c-45c9-b41d-6f4c47cbda03" /> </p>

## Switch là gì?
Switch là thiết bị chuyên dụng được dùng để kết nối các thiết bị lại với nhau bằng cáp Ethernet. Những thiết bị này được cắm vào các cổng (port) của Switch, một Switch tuỳ quy mô sử dụng sẽ có số cổng khác nhau ví dụ như ở quy mô phòng học máy tính thì thường có từ 24 cho tới 48 cổng. 

Switch có hiệu năng vượt trội hơn so với các thiết bị cùng loại như Hub hay Repeater vì nó xây một bảng ghi nhớ địa chỉ MAC (MAC Address Table). Nó có thể biết được là cổng này đang kết nối với địa chỉ MAC của máy nào, nên khi nhận được gói tin thì Switch có thể truyền tới đúng máy giúp tối ưu lưu lượng còn các thiết bị khác thì thường truyền cho tất cả các máy đang kết nối luôn.

<p align="center"><img width="760" height="475" alt="image" src="https://github.com/user-attachments/assets/4421f73f-35da-496a-ad4b-78c6b5c96ca2" /></p>

Bên cạnh đó, Router và Switch có thể kết nối lại với nhau, điều này cho phép tăng cường khả năng dự phòng trong một mạng lưới khi không phụ thuộc vào một nhánh chính mà ta có thể tách ra nhiều nhánh nhỏ, nếu như Switch bên này có vấn đề gì đó thì không ảnh hưởng tới các bên còn lại. Tuy làm việc này có thể tăng lượng thời gian gói tin truyền tải tới, nhưng đánh đổi để mạng không bị sấp hoàn toàn khi có vấn đề vẫn tốt hơn.

## Router là gì?
Router là thiết bị kết nối các mạng với nhau (Ví dụ như mạng LAN của nhà chúng ta với Internet của ISP) và truyền dữ liệu giữa chúng bằng việc định tuyến. Khác với Switch sử dụng địa chỉ MAC để kết nối và truyền tải dữ liệu trong một mạng LAN, Router sử dụng địa chỉ IP để xác định dữ liệu cần truyền đến với mạng nào. Định tuyến (routing) là thuật ngữ nói về việc truyền dữ liệu giữa các mạng, nó bao gồm việc tạo đường truyền rồi chọn đường truyền tối ưu nhất để kết nối các mạng rồi truyền dữ liệu. Định tuyến sẽ hữu ích khi ta sử dụng nhiều đường dẫn như hình dưới.

<p align="center"><img width="1140" height="390" alt="image" src="https://github.com/user-attachments/assets/eed2befd-4923-4758-81c7-7bc37cad90cf" /> </p>

## Chia mạng con (Subnetting)
Như chúng ta tìm hiểu trước đó thì một mạng máy tính có thể có đủ hình dạng và kích thước, từ to đến nhỏ, từ hình sao tới hình vòng. Subnetting là thuật ngữ chỉ việc chia một mạng thành các mạng nhỏ hơn, gọn hơn bên trong mạng đó. Hình dung nó như việc chia bánh kem, chỉ có một lượng bánh nhất định thôi nhưng ai cũng muốn thì phải chia nhỏ ra. Subnetting là việc ta quyết định ai sẽ nhận được miếng bánh nào, và chỉ dành riêng miếng bánh đó cho người đó.

Giả sử ta có một doanh nghiệp, trong đó có các phòng ban như:
- Kế toán
- Tài chính
- Nhân sự

<p align="center"><img width="908" height="801" alt="image" src="https://github.com/user-attachments/assets/bde8453c-c195-4ffb-bec1-b428e64576ef" /></p>

Và trong thực tế, ta cần phải biết dữ liệu này cần được gửi đến phòng ban nào để xử lí vì vậy hệ thống mạng cũng cần phải thực thi được như vậy. Những quản trị viên mạng sẽ chia các mạng con (subnetting) ra phục vụ cho những nhu cầu này, như phòng tài chính sẽ có một mạng riêng, phòng kế toán một mạng riêng,..

Subnetting được thực hiện bằng cách phân chia số lượng thiết bị có thể sử dụng mạng, được biểu diễn bằng con số cụ thể gọi là subnet mask (mặt nạ mạng con). Như chúng ta đã tìm hiểu trước đó thì một địa chỉ IP sẽ chia ra 4 phần và mỗi phần được gọi là octet. Và subnet mask cũng có cấu trúc tương tự.

<p align="center"><img width="1140" height="488" alt="image" src="https://github.com/user-attachments/assets/a95fd9e8-6eef-4908-be9e-05cab367b5fd" /> </p>

Các mạng con sẽ sử dụng địa chỉ IP với mục đích:
- Xác định địa chỉ mạng (Network Address)
- Xác định địa chỉ host (Host Adress)
- Xác định cổng mặc định (Default Gateway)

| Loại          | Giải thích                                                                                                                                                               | Ví dụ                                                                                                                                                                                                                      |
|---------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Địa chỉ Mạng  | Đây là địa chỉ đại diện cho cả mạng, không gán vào bất cứ thiết bị nào và được lấy bằng cách tách phần mạng trong IP và đặt phần host thành 0                            | Ví dụ một thiết bị kết nối mạng có IP là 192.168.1.100 thì địa chỉ mạng là 192.168.1.0                                                                                                                                     |
| Địa chỉ Host  | Đây là địa chỉ IP, gán cho một thiết bị cụ thể trong mạng                                                                                                                | Ví dụ một thiết bị kết nối mạng có IP là 192.168.1.100                                                                                                                                                                       |
| Cổng mặc định | Đây là địa chỉ được gọi là cửa ngõ để đi ra khỏi mạng con, nó thường là địa chỉ của Router. Bất kì thiết bị nào đi ra khỏi mạng con thì phải bước qua địa chỉ này trước. | Ví dụ thiết bị trong LAN muốn đi ra Internet thông qua Router thì cần phải truy cập 192.168.1.254. Một địa chỉ cổng mặc định có thể là bất kì địa chỉ host nào nhưng thường nó sẽ lấy địa chỉ đầu hoặc cuối (.1 hoặc .254) |

Hiện nay thì quy mô mạng trong nhà ít khi triển khai subnetting vì tối đa 254 thiết bị kết nối mạng là quá nhiều rồi, còn quy mô doanh nghiệp thì mới cần vì trong đó triển khai rất nhiều thiết bị như máy in, PC, camera, TV,.. Khi ấy, subnetting sẽ cung cấp rất nhiều lợi ích như tính bảo mật, ổn định và toàn quyền quản lí. 

Ví dụ như trong một quán cafe, ta có thể chia ra 2 nhánh mạng con:
- Cái dành cho nhân viên, phục vụ cho các việc quản lí, tính toán, theo dõi,..
- Cái dành cho khách hàng, để khách tới mua nước sẽ được sử dụng mạng miễn phí

Nếu như ta không chia mạng ra thì những thông tin nội bộ rất dễ bị người ngoài khai thác được.

## ARP (Address Resolution Protocol)
Là công nghệ cho phép các thiết bị tìm ra địa chỉ MAC của thiết bị khác khi đã biết IP trong cùng một mạng, vì trong LAN thì các thiết bị trong mạng muốn trao đổi các gói tin thông qua Switch sẽ cần xác định được địa chỉ MAC. Khi có 1 thiết bị muốn giao tiếp với thiết bị khác, nó sẽ gửi ARP Request (broadcast) đến toàn bộ các máy trong mạng cùng lúc để hỏi "địa chỉ IP này là của địa chỉ MAC nào?". Khi đó máy cần tìm nhận được tin sẽ trả về một ARP Reply (unicast) về cho đúng máy hỏi. Từ đó thiết bị hỏi có thể nhớ được thiết bị nó tìm có địa chỉ MAC là gì bằng cách lưu vào ARP Cache. ARP Cache sẽ giúp mỗi thiết bị trong mạng duy trì được thông tin của các thiết bị khác, từ đó mỗi lần cần tìm địa chỉ MAC sẽ không cần hỏi toàn bộ thiết bị trong mạng nữa.

<p align="center"><img width="823" height="864" alt="image" src="https://github.com/user-attachments/assets/a2f17643-f27b-4f5e-9861-ff683a9eeacb" /></p>



