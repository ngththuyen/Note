## picoCTF
### GET aHEAD
- Sau khi launch, truy cập vào thì thấy là 1 site có 2 nút, nhấn nút "Choose Red" thì nền hoá đỏ, title đổi thành "Red".
<img width="1366" height="641" alt="image" src="https://github.com/user-attachments/assets/acb9fd65-d2ad-4ae6-9a0e-9bef39182b41" />

- "Choose Blue" thì tương tự nhưng mà là Blue
<img width="1366" height="641" alt="image" src="https://github.com/user-attachments/assets/4bcfbb52-5bf1-4986-903e-ae984c513e10" />

- Mở mã nguồn của site, ta có thể thấy cái nút chọn màu đỏ là dùng method **GET** còn xanh là **POST**, còn lại nhìn chung là liên quan tới giao diện, ko có gì khác
<img width="1327" height="681" alt="image" src="https://github.com/user-attachments/assets/bd6c5efc-d403-494c-afc0-d79f43e41d22" />

- Thử truy cập vào css mà site href tới, trông lộn xộn như thế này khả năng cao không có thông tin gì tại bài này là bài cơ bản nên nhét thông tin trong này newbie mò đằng trời
<img width="1366" height="691" alt="image" src="https://github.com/user-attachments/assets/bff36bfc-bbe1-4405-a487-5c7af3c5fe83" />

- Đã khai thác gần như xong hết các thông tin cơ bản, vì topic bài này liên quan tới HTTP Request theo anh Đức bảo nên thử bật BurpSuite để đọc thông tin khi nhấn 2 cái nút trên xem sao.
- Khi nhấn nút Red thì cả Header Request lẫn Response chả có gì đặc biệt, hầu như là các thông tin cơ bản, nhìn vào URL khi nhấn nút GET cũng ko thấy thông tin gì bổ sung cho request đó
<img width="1366" height="697" alt="image" src="https://github.com/user-attachments/assets/e125dc11-eebe-4e05-9466-5f61f556e62c" />

- Thử với nút Blue, method lần này là POST nhưng lại một lần nữa là ko có thông tin gì kể cả bên trong Body
<img width="1365" height="614" alt="image" src="https://github.com/user-attachments/assets/ca7ab627-5aed-410f-b84b-bbaa61cb18ab" />

- Khá bí, không còn biết hướng nào để thử, quay lại đề bài và mở 2 cái hint thì ý 1 nó bảo là ngoài 2 cái nút trên thì có lẽ còn cái nút khác và ý 2 thì nó kêu thử chỉnh request trên Burpsuite rồi nhìn response
<img width="707" height="196" alt="image" src="https://github.com/user-attachments/assets/89b06545-0c4a-4dfd-9f5d-877e1929f943" />

- Nhìn lại cái đề bài, nó tên là "GET aHEAD", kết hợp với các hint, thử gửi một Request HEAD xem sao, tính chất của Method này giống GET nên thử copy nội dung của 1 Request GET rồi đổi type thành HEAD
<img width="1366" height="488" alt="image" src="https://github.com/user-attachments/assets/2993bf0c-3b15-4344-bcec-934e76ffe12e" />

- Hoàn thành bài, ta lấy được flag là `academy{r3j3ct_th3_du4l1ty_57f62d9}` trên header của Response. Khá buồn khi không thể tự tìm ra mà phải nhờ vào hint để xử lí

<img width="1345" height="529" alt="image" src="https://github.com/user-attachments/assets/0cd161ee-816d-466b-894d-9ad7cc45f1ff" />





