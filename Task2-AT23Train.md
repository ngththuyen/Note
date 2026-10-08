<p align="center"><img align="center" width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/e6db8fc1-388a-4fe1-a36d-f16173e4b753" /></p>

## picoCTF
### [GET aHEAD](https://learn.cylabacademy.org/library/132)
Sau khi launch, truy cập vào thì thấy là 1 site có 2 nút, nhấn nút "Choose Red" thì nền hoá đỏ, title đổi thành "Red".

<img width="1366" height="641" alt="image" src="https://github.com/user-attachments/assets/acb9fd65-d2ad-4ae6-9a0e-9bef39182b41" />

"Choose Blue" thì tương tự nhưng mà là Blue

<img width="1366" height="641" alt="image" src="https://github.com/user-attachments/assets/4bcfbb52-5bf1-4986-903e-ae984c513e10" />

Mở mã nguồn của site, ta có thể thấy cái nút chọn màu đỏ là dùng method **GET** còn xanh là **POST**, còn lại nhìn chung là liên quan tới giao diện, ko có gì khác

<img width="1327" height="681" alt="image" src="https://github.com/user-attachments/assets/bd6c5efc-d403-494c-afc0-d79f43e41d22" />

Thử truy cập vào css mà site href tới, trông lộn xộn như thế này khả năng cao không có thông tin gì tại bài này là bài cơ bản nên nhét thông tin trong này newbie mò đằng trời

<img width="1366" height="691" alt="image" src="https://github.com/user-attachments/assets/bff36bfc-bbe1-4405-a487-5c7af3c5fe83" />

Đã khai thác gần như xong hết các thông tin cơ bản, vì topic bài này liên quan tới HTTP Request theo anh Đức bảo nên thử bật BurpSuite để đọc thông tin khi nhấn 2 cái nút trên xem sao. Khi nhấn nút Red thì cả Header Request lẫn Response chả có gì đặc biệt, hầu như là các thông tin cơ bản, nhìn vào URL khi nhấn nút GET cũng ko thấy thông tin gì bổ sung cho request đó

<img width="1366" height="697" alt="image" src="https://github.com/user-attachments/assets/e125dc11-eebe-4e05-9466-5f61f556e62c" />

Thử với nút Blue, method lần này là POST nhưng lại một lần nữa là ko có thông tin gì kể cả bên trong Body

<img width="1365" height="614" alt="image" src="https://github.com/user-attachments/assets/ca7ab627-5aed-410f-b84b-bbaa61cb18ab" />

Khá bí, không còn biết hướng nào để thử, quay lại đề bài và mở 2 cái hint thì ý 1 nó bảo là ngoài 2 cái nút trên thì có lẽ còn cái nút khác và ý 2 thì nó kêu thử chỉnh request trên Burpsuite rồi nhìn response

<img width="707" height="196" alt="image" src="https://github.com/user-attachments/assets/89b06545-0c4a-4dfd-9f5d-877e1929f943" />

Nhìn lại cái đề bài, nó tên là "GET aHEAD", kết hợp với các hint, thử gửi một Request HEAD xem sao, tính chất của Method này giống GET nên thử copy nội dung của 1 Request GET rồi đổi type thành HEAD

<img width="1366" height="488" alt="image" src="https://github.com/user-attachments/assets/2993bf0c-3b15-4344-bcec-934e76ffe12e" />

Hoàn thành bài, ta lấy được flag là `academy{r3j3ct_th3_du4l1ty_57f62d9}` trên header của Response. Khá buồn khi không thể tự tìm ra mà phải nhờ vào hint để xử lí

<img width="1345" height="529" alt="image" src="https://github.com/user-attachments/assets/0cd161ee-816d-466b-894d-9ad7cc45f1ff" />

### [Cookies](https://learn.cylabacademy.org/library/173)
Mở ra là 1 site có nút home, trung tâm có một thanh search sử dụng method POST với placeholder là snickerdoodle

<img width="1366" height="641" alt="image" src="https://github.com/user-attachments/assets/58748e6c-25a3-451f-b8d0-5b03ddb8194e" />

Điền đại vào gtri nào đó thì nó trả về thông báo đỏ "That doesn't appear to be a valid cookie."

<img width="1366" height="641" alt="image" src="https://github.com/user-attachments/assets/e379e2c1-00ad-45d8-a485-2ab81975202d" />

Thử điền giá trị snickerdoodle của placeholder thì nó ra màn hình "I love snickerdoodle cookies!" và thông báo xanh là "That is a cookie! Not very special though..."

<img width="1366" height="641" alt="image" src="https://github.com/user-attachments/assets/a8f6234b-21b2-4c61-bac1-c97ee58e5dfc" />

Kiểm tra mã nguồn, nó có một comment là  `<!-- Categories: success (green), info (blue), warning (yellow), danger (red) -->` ngoài nó ra thì ko có gì đặc biệt, có vẻ giá trị của placeholder này chả có gì

<img width="1366" height="689" alt="image" src="https://github.com/user-attachments/assets/6e13abe2-277c-4ea1-994e-bc82b84dc608" />

Dùng dev tool, vào phần cookie thì thấy 1 cookie tên là "name", giá trị cookie khi ta ở page home và page nhập sai là -1, giá trị khi ở page nhập đúng placeholder là 0, thử đổi value sang 1 và reload trang kết quả sau khi nhập placeholder thì nó ghi là "I love chocolate chip cookies!", thử đổi value sang 2 thì nó ghi là "I love oatmeal raisin cookies!", thử đổi value sang 3 là "I love gingersnap cookies!",... lười duyệt từng thằng quá nên duyệt từ trên xuống để tìm max, check từ 50,40,30 ko thấy, tới 20 thì thấy, thử giảm 30 xuống 29,28 thì 28 là gtri là "I love white chocolate macadamia cookies!". Điều này cho thấy mỗi loại bánh là 1 giá trị cookie khác nhau

<img width="1362" height="683" alt="image" src="https://github.com/user-attachments/assets/1816bcee-2423-413c-b5ee-79fe464d54f6" />

Không còn thông tin nào khác, thử mở Burpsuite xem khi search thì các thông điệp http sẽ có những thông tin gì. Nhìn log thì thấy sau khi điền 1 gtri đúng vào thanh r search thì nó sẽ set name bằng đúng số của tên cookie đó, sau đó chuyển hướng user sang page /check, ở page này thì nó cũng set cookie những mà là session= gì đó ko hiểu lắm (mấy bài đầu chắc ko đánh đố phần này đâu)

<img width="1366" height="690" alt="image" src="https://github.com/user-attachments/assets/f5e79bc7-6bc9-48c4-9d14-afe3fb3eda6a" />

Sau khi xem các thông điệp của request và response ko có gì mới thì lại quay lại cái duyệt từng giá trị cookie, burpsuite có tool là Intruder, duyệt các giá trị cookie khi nãy đã biết min và max, set position là cái value của cookie "name", set type attack là sniper, payload type là number, range 3-28, squential

<img width="1337" height="572" alt="image" src="https://github.com/user-attachments/assets/faba2d59-8866-4776-bbf0-bb45337a25b1" />

Duyệt hết thì thấy có 1 đoạn response length khá ngắn trông khá nghi tại value = 18, vào check thì ra flag `academy{3v3ry1_l0v3s_c00k135_90a3a7cb}`

<img width="1366" height="705" alt="image" src="https://github.com/user-attachments/assets/a3bc13bf-3700-4814-bf7e-4ae332fb52b7" />

## Root-me
### [HTTP - IP restriction bypass](https://www.root-me.org/en/Challenges/Web-Server/HTTP-IP-restriction-bypass)
Mở site ra, nó là 1 giao diện login kèm một số thông tin, dòng đầu là **"Your IP ::ffff:113.177.143.125 do not belong to the LAN."** tức nó bảo IP mày không thuộc mạng nội bộ, dòng 2 là "Intranet", dòng 3,4,5 là form login cơ bản, và dòng 6 là **"You should authenticate because you're not on the LAN."** Tức yêu cầu của bài này là phải tìm cách nào đó biến IP của mình thành IP nội bộ được cho phép mới truy cập được, hoặc là sẽ dùng chức năng đăng nhập mới vào được

<img width="939" height="359" alt="image" src="https://github.com/user-attachments/assets/f9687274-0d63-49d7-909d-4dd2e13b77c3" />

Thử điền đại thông tin vào form, nhấn vào thấy chả có thông báo gì hết 

<img width="853" height="323" alt="image" src="https://github.com/user-attachments/assets/b12da30d-a78a-4317-80bf-465b84f9f988" />

Check mã nguồn, thấy được thông tin là form này là dùng method POST, action trỏ vào chính site hiện tại, 

<img width="1245" height="511" alt="image" src="https://github.com/user-attachments/assets/0f6a0876-e9fa-496d-8964-4aeef0e7c906" />

Mở thử file s.css, có vẻ khôgn có thông tin nào khác ngoài trang trí

<img width="1112" height="572" alt="image" src="https://github.com/user-attachments/assets/36402014-b5ed-47f6-a686-6778d17d9dfd" />

Mở thử https://www.root-me.org/?page=externe_header thì thấy đây là cái logo của web làm bài chứ ko có gì

Mở burpsuite, thửu điền đại gtri vào form rồi submit xem có thông tin gì ko. Xem qua thì chả có gì khai thác được, có vẻ chức năng đặng nhập này phế, buộc phải kiếm cách thay đổi IP

<img width="1259" height="475" alt="image" src="https://github.com/user-attachments/assets/0508fe83-c3a3-415b-9db4-8609dbbb9a8e" />

Như đề bài nói: 
"Dear colleagues,
We’re now managing connections to the intranet using private IP addresses, so it’s no longer necessary to login with a username / password when you are already connected to the internal company network.
Regards,
The network admin"

Giờ phải kiếm cách nào vào được mạng nội bộ hoặc là gỡ bỏ lớp kiểm tra đó. Tra gg thì thấy có một số request header như X-Forwarded-For: có thể set được IP của người gửi, thử set thành ip của localhost trong gói tin GET khi truy cập vào site xem sao. Thử với đúng X-Forwarded-For: 127.0.0.1 thì page có thay đổi nội dung thật mà chả hiểu sao nó vẫn ko ra flag, thử một số đại lượng khác xem

<img width="1350" height="553" alt="image" src="https://github.com/user-attachments/assets/45684593-76fc-4a4c-be13-15c00fc566ca" />

Xem thông tin ở trang gốc thì IP nó là kiểu định dạng gì ấy (::ffff:113.177.143.125), tức là muốn vô thì phải dùng ip localhost theo đúng dạng của nó. Tra AI thì dạng IP này là dạng kết hợp giữa v4 và v6, hiểu đơn giản thì mấy cái số sau dấu : cuối cùng là ipv4, giờ thử ::ffff:127.0.0.1 theo format của nó xem

<img width="1346" height="542" alt="image" src="https://github.com/user-attachments/assets/66cf6a41-0512-4041-a969-0bbb1c071738" />

Vẫn ko ra kết quả gì, có thế ip localhost nó ko phải là 127.0.0.1 mà nó là số nào đó nằm trong phạm vi ip local, thử dùng tool để duyệt trâu xem nhưng tính sương sương thế 3 vị trí từ 0-255 là 255^3 tức 16581375 trường hợp có vẻ ko ổn lắm khi mỗi lần gửi cũng tốn 5-10s rồi. Đi vào ngõ cụt nên dẹp hêt mở lại đề bài, ngồi đọc kĩ, thấy họ có phần **related resourese**.

<img width="1304" height="446" alt="image" src="https://github.com/user-attachments/assets/9541dba6-a746-4c68-9083-29d69dc03ce0" />

Toàn tiếng anh đọc chả hiểu gì nên mò đại mấy cái IPV4 trong đó rồi đưa vào request header thử, chả hiểu sao lại ra kết quả luôn, quá nhảm chả hiểu sao page là định dạng IP gì đó mà result là ipv4, cũng ko hiểu sao 127.0.0.1 lại ko được, passw là **Ip_$po0Fing**

<img width="1289" height="582" alt="image" src="https://github.com/user-attachments/assets/317d61a4-2bda-42c0-bab0-82183f8c9d3f" />

Sau khi tìm hiểu sâu thì mới nhận ra bài này qua được là vì tài liệu kia nó nói về dải IP trong mạng nội bộ mang tên RFC 1918, tức vì đề bài nói về mạng trong tổ chức nên sẽ sử dụng dải này, còn cái 127.0.01 kia chỉ là ip riêng của từng máy thôi, nó tự gọi chính nó, nên ko được. 

<img width="1200" height="602" alt="image" src="https://github.com/user-attachments/assets/915c3c01-550f-4fcf-9d16-1d01affe6021" />

### [HTTP - User-agent](https://www.root-me.org/en/Challenges/Web-Server/HTTP-User-agent)
Mô tả của bài: "Admin is really dumb...", không có gì hữu ích

Mở site, thấy chỉ xuất hiện một dòng "Wrong user-agent: you are not the "admin" browser!", để bài cũng đề cập "user-agent". Có vẻ đó là thông tin xoay quanh bài này

<img width="1095" height="304" alt="image" src="https://github.com/user-attachments/assets/0e1d19f1-1a00-49c2-a577-0b23eeb6bfb3" />

Check src html, thấy chỉ có thẻ h3 chứa thông tin ở trên chứ ko còn gì khác, có vẻ bài này sẽ liên quan tới header user-agent

<img width="1236" height="282" alt="image" src="https://github.com/user-attachments/assets/1a888100-6b47-4c56-9649-abf3b2da52fb" />

Check cookie, network từ devtool thì ko có thông tin gì đặc biệt

<img width="1282" height="416" alt="image" src="https://github.com/user-attachments/assets/81cc6be9-596a-4e95-a68b-bcb273a1d402" />

Mở burpsuite, dùng Proxy, check history khi truy cập web lần đầu sau đó send request GET đó cho repeater rồi thử đổi user-agent sang "admin" như site bảo xem nó trả về gì

<img width="1312" height="561" alt="image" src="https://github.com/user-attachments/assets/664b03aa-f63b-45d1-ac07-67ac31ecfc7a" />

Và đúng như dự đoán, ra luôn kết quả là **rr$Li9%L34qd1AAe27**, bài này khá đơn giản khi các thông tin đều đã chỉ về việc thay đổi header request

### [HTTP - Headers](https://www.root-me.org/en/Challenges/Web-Server/HTTP-Headers)
"HTTP response give informations
Get an administrator access to the webpage"

Mở site ra thì xuất hiện 1 dòng có nội dung là "Content is not the only part of an HTTP response!", nghĩa là nội dung ko phải là phần duy nhất của response, ý của nó chắc là thằng response có nhiều thứ khác ngoài nội dung

<img width="970" height="387" alt="image" src="https://github.com/user-attachments/assets/085bca80-f7a8-453a-a255-c105a115e340" />

Kiểm tra src html,css, tương tự như bài trên là nó cũng chả có cái gì

<img width="1178" height="441" alt="image" src="https://github.com/user-attachments/assets/3de29081-4e9b-4eb0-a3cc-464d67851a24" />

Như đề bài có để cập về response, mở dev tool check phần network rồi F5 xem response có gì đặc biệt. Và đúng như dự đoán, ở đây có 1 header response khá lạ là header-rootme-admin đang mang giá trị none, đây là thứ cần phải khai thác

<img width="1280" height="550" alt="image" src="https://github.com/user-attachments/assets/b4ea22b8-009c-47ca-8bea-422c5f4a8c4f" />

Mở burpsuite xem cho rõ, tuy nhiên quả header này là ở phía response, ta ko thể tự tuỳ chỉnh kết quả của server trả về mà chỉ chỉnh được cái gửi đi. Thử copy nguyên header đó rồi nhét vào header request xem sao

<img width="1275" height="527" alt="image" src="https://github.com/user-attachments/assets/cc53034c-3121-4688-9d2b-e54e4b9d649d" />

Ra kết quả thật, passw là **HeadersMayBeUseful**, nhưng vẫn không hiểu ý nghĩa challenge này lắm khi chỉ cần copy header response rồi đưa vào request

### [HTTP - POST](https://www.root-me.org/en/Challenges/Web-Server/HTTP-POST)
"Do you know HTTP?
Find a way to beat the top score!"

Mở site thì thấy là một trang nội dung liên quan tới game Human vs Machine

<img width="978" height="353" alt="image" src="https://github.com/user-attachments/assets/0d1589be-3e88-44d8-ac63-606679651361" />

Nó yêu cầu mình phải được 999999 mới thắng, khi thử nhấn cái nút Give a try thì nó bốc random số gì đó. VD một kqua trả về "Hoo tooooo sad, you lost. Your score: 791839! I'm always the best :)"

<img width="889" height="319" alt="image" src="https://github.com/user-attachments/assets/d16e1f19-049b-4c22-9574-1dc35d1205b6" />

Check src html, thấy cái form nút random đó sử dụng một đoạn mã js gán vào input name "score" với nội dung là "document.getElementsByName('score')[0].value = Math.floor(Math.random() * 1000001)". Nhìn sơ qua thì nó dùng hàm random rồi nhân 1000001, nếu tích đó là 999999 thì qua, khá md khi cái hàm rand đó chỉ trả về  0 <= x < 1 (AI bảo thế)

<img width="1162" height="503" alt="image" src="https://github.com/user-attachments/assets/04e0ca36-4c87-4bdd-853d-f9e6c9f77691" />

Vì form nó ko giấu gì hết nên nhìn qua ta có thể thử với idea là gửi request POST rồi send sang repeater và đổi value input "score" sang 999999. Có idea rồi, mở burpsuite và triển thôi, tuy nhiên có vẻ idea này ko đúng, thử set score đúng như nó yêu cầu rồi nhưng mà sau khi POST thì nó vẫn chả ra kết quả

<img width="1198" height="587" alt="image" src="https://github.com/user-attachments/assets/ab3a74fa-d489-4592-a4d1-93e3d28accdd" />

À có vẻ hơi ngu, đọc ko kĩ đề tưởng là phải = 999999 nhưng xem lại thì nó yêu cầu là phải đánh bại machine tức score phải lớn hơn, thử lại với 1000000 thì đúng là đã ra flag **H7tp_h4s_N0_s3Cr37S_F0r_y0U**

<img width="1345" height="512" alt="image" src="https://github.com/user-attachments/assets/ccf256df-863f-49f9-af5c-665565e66f4e" />

## Hoàn thành task 😭

<img width="1159" height="631" alt="image" src="https://github.com/user-attachments/assets/6265189b-a356-477c-968d-2842d923e6b5" />
<img width="880" height="478" alt="image" src="https://github.com/user-attachments/assets/eed700a2-8c49-4e0d-85ba-99600ba3ec74" />






