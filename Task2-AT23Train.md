<p align="center"><img align="center" width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/e6db8fc1-388a-4fe1-a36d-f16173e4b753" /></p>

## picoCTF
### [GET aHEAD](https://learn.cylabacademy.org/library/132)
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

### [Cookies](https://learn.cylabacademy.org/library/173)
- Mở ra là 1 site có nút home, trung tâm có một thanh search sử dụng method POST với placeholder là snickerdoodle
<img width="1366" height="641" alt="image" src="https://github.com/user-attachments/assets/58748e6c-25a3-451f-b8d0-5b03ddb8194e" />

- Điền đại vào gtri nào đó thì nó trả về thông báo đỏ "That doesn't appear to be a valid cookie."
<img width="1366" height="641" alt="image" src="https://github.com/user-attachments/assets/e379e2c1-00ad-45d8-a485-2ab81975202d" />

- Thử điền giá trị snickerdoodle của placeholder thì nó ra màn hình "I love snickerdoodle cookies!" và thông báo xanh là "That is a cookie! Not very special though..."
<img width="1366" height="641" alt="image" src="https://github.com/user-attachments/assets/a8f6234b-21b2-4c61-bac1-c97ee58e5dfc" />

- Kiểm tra mã nguồn, nó có một comment là  `<!-- Categories: success (green), info (blue), warning (yellow), danger (red) -->` ngoài nó ra thì ko có gì đặc biệt, có vẻ giá trị của placeholder này chả có gì
<img width="1366" height="689" alt="image" src="https://github.com/user-attachments/assets/6e13abe2-277c-4ea1-994e-bc82b84dc608" />

- Dùng dev tool, vào phần cookie thì thấy 1 cookie tên là "name", giá trị home và nhập sai là -1, giá trị khi nhập đúng placeholder là 0, thử đổi value sang 1 và reload trang kết quả sau khi nhập placeholder thì nó ghi là "I love chocolate chip cookies!", thử đổi value sang 2 thì nó ghi là "I love oatmeal raisin cookies!", thử đổi value sang 3 là "I love gingersnap cookies!",... lười duyệt từng thằng quá nên duyệt từ trên xuống để tìm max, check từ 50,40,30 ko thấy, tới 20 thì thấy, thử giảm 30 xuống 29,28 thì 28 là gtri là "I love white chocolate macadamia cookies!". Điều này cho thấy mỗi loại bánh là 1 giá trị cookie khác nhau
<img width="1362" height="683" alt="image" src="https://github.com/user-attachments/assets/1816bcee-2423-413c-b5ee-79fe464d54f6" />

- Không còn thông tin nào khác, thử mở Burpsuite xem khi search thì các thông điệp http sẽ có những thông tin gì. Nhìn log thì thấy sau khi điền 1 gtri đúng vào thanh r search thì nó sẽ set name bằng đúng số của tên cookie đó, sau đó chuyển hướng user sang page /check, ở page này thì nó cũng set cookie những mà là session= gì đó ko hiểu lắm (mấy bài đầu chắc ko đánh đố phần này đâu)
<img width="1366" height="690" alt="image" src="https://github.com/user-attachments/assets/f5e79bc7-6bc9-48c4-9d14-afe3fb3eda6a" />

- Sau khi xem các thông điệp của request và response ko có gì mới thì lại quay lại cái duyệt từng giá trị cookie, burpsuite có tool là Intruder, duyệt các giá trị cookie khi nãy đã biết min và max, set position là cái value của cookie "name", set type attack là sniper, payload type là number, range 3-28, squential
<img width="1337" height="572" alt="image" src="https://github.com/user-attachments/assets/faba2d59-8866-4776-bbf0-bb45337a25b1" />

- Duyệt hết thì thấy có 1 đoạn response length khá ngắn trông khá nghi tại value = 18, vào check thì ra flag `academy{3v3ry1_l0v3s_c00k135_90a3a7cb}`
<img width="1366" height="705" alt="image" src="https://github.com/user-attachments/assets/a3bc13bf-3700-4814-bf7e-4ae332fb52b7" />

## Root-me













