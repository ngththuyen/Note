<img width="453" height="113" alt="image" src="https://github.com/user-attachments/assets/9032e9e0-e43e-4124-a6f3-409808faaed5" />## OverTheWire: Bandit
### Lvl 0
Đề yêu cầu phải tìm hiểu về SSH để kết nối vào host có Domain là `bandit.labs.overthewire.org` và Port là `2220`, username là `bandit0` và passw là `bandit0`. Bài này ta dùng lệnh SSH với pháp cơ bản là `ssh <username>@<domain> -p <port>`.

<img width="716" height="336" alt="image" src="https://github.com/user-attachments/assets/1ecfe8b7-eac9-48a8-b2ac-7fdb488cb1e2" />

Sau khi dùng lệnh thì nó sẽ yêu cầu điền mật khẩu, ta điền đúng với mk đề đã cấp thì sẽ truy cập được 

<img width="875" height="494" alt="image" src="https://github.com/user-attachments/assets/4d59e4a6-a4c2-440d-b803-077664e0fe62" />

### Lvl 0-1
Mục tiêu của bài này là tìm được file `readme` ở thư mục `home`, trong đó sẽ có passw để SSH vào bài tiếp theo. Ta dùng lệnh `pwd` để kiểm tra hiện tại đang đứng ở đâu thì nó trả về `home/bandit0`, thử dùng `ls` thì thấy được là trong nơi ta đang đứng có chứa file tên `readme`.

<img width="405" height="147" alt="image" src="https://github.com/user-attachments/assets/d0fc89e1-bc77-4d11-a9be-53e0955f16b6" />

Ta dùng lệnh `cat` để đọc file đó thì thu được passw cho màn tiếp theo là `6y2kwnwK6grgvwvpvLaa2T1cpFEKOhNR`. 

<img width="898" height="264" alt="image" src="https://github.com/user-attachments/assets/f75431b4-34aa-414a-86d1-202abae694d3" />

### Lvl 1-2
Sau khi tìm đc passw để SSH bài mới từ bài trước, ta exit SSH hiện tại thông qua lệnh `exit`

<img width="595" height="197" alt="image" src="https://github.com/user-attachments/assets/6f7a5800-6f29-4603-a1de-95332392b7f8" />

Sau đó kết nối SSH vào bài tiếp theo, giờ đây username sẽ đổi thành `bandit1` còn passw thì như ở trên đã tìm ra, các nội dung khác giữ nguyên 

<img width="755" height="315" alt="image" src="https://github.com/user-attachments/assets/2e261a3d-4683-4d25-9648-c50080e19d00" />

Kết nối được vào rồi thì đọc đề màn này nó bảo passw nằm trong file tên là `-`, tức tên file chỉ có kí tự đó. Cũng dùng `ls` thì thấy file tên `-` đang ở thư mục hiện tại. Thử dùng lệnh `cat -` thì có vẻ không hoạt động như ý

<img width="419" height="157" alt="image" src="https://github.com/user-attachments/assets/b1a88187-b0cf-4e94-bb91-e4bb0b663f46" />

Sau đó thử chèn mấy kí tự như "" hay '' vào - thì cũng ko hoạt động, đến khi thay bằng `cat ./-` thì mới có thể đọc được. Ý nghĩa của lệnh này là cái `.` tức là ở vị trí hiện tại còn cái sau dấu `/` là tên file muốn đọc. Từ đó ra passw là `PK8fYLZg2hnHSz83plBL1iEPKdD3QToB`

<img width="455" height="365" alt="image" src="https://github.com/user-attachments/assets/f3fe822e-9aa4-4bb4-8245-2594dcc0ca57" />

### Lvl 2-3
Tương tự như bài trước exit r SSH, lần này sẽ kết nối vào usrname `bandit2` rồi passw tìm đc ở trên. Bài này đề nó bảo là passw nằm trong file có dấu cách mang tên `--spaces in this filename--` ở thư mục `home`. Thử dùng `ls` thì có quả tên file kiểu đó thật

<img width="416" height="105" alt="image" src="https://github.com/user-attachments/assets/99b665e2-f8a6-4fdc-8452-bdde084be61f" />

Cũng tiếp tục thử với "" '' và ./ thì như kỳ vòng là đã ra kết quả. Passw là `7ZZ2LFrykP2zEyvBl4m3clcL7tGYJPME`. Nguyên nhân 2 lệnh đầu nó ko hoạt động có vẻ là nó nhận `--` làm tham số, còn lệnh 3 thì có `./` thì nhìn phát cat nó biết là dường dẫn.

<img width="983" height="468" alt="image" src="https://github.com/user-attachments/assets/3f08104a-81fb-455a-b964-3de7fcfc36fe" />

Hoặc ta cũng có thể thử như tip nó bảo là thêm `--` vào để pass khoảng trắng, nhma tip có vẻ hơi cùi khi nó nhầm là mở nhiều file, phải bổ sung thêm '' thì mới hoạt động

<img width="1101" height="497" alt="image" src="https://github.com/user-attachments/assets/0cf0d954-03c6-4a68-80c4-8158b227372f" />

### Lvl 3-4
Bài này thì nó bảo là passw nằm ở trong 1 file ẩn ở trong thư mục `inhere`, dùng `ls` ở vị trí hiện tại thì thấy 1 folder `inhere`. Ta `cd` vào rồi dùng `ls` tiếp thì ko thấy bất cứ thứ gì như đề bảo thật, file passw đã bị ẩn.

<img width="450" height="174" alt="image" src="https://github.com/user-attachments/assets/1fccfd84-f9ba-456c-b895-a5a1b7f4434b" />

Ta dùng lệnh `ls --help` xem có option gì khác để check không thì thấy có tham số `-a` là sẽ có tác dụng ko bỏ qua file bị ẩn.

<img width="1329" height="444" alt="image" src="https://github.com/user-attachments/assets/209e039e-2a50-4be2-87f7-cd6b0d5e616d" />

Dùng `ls -a` thì đúng thật là xuất hiện thêm các folder/file khác. Thử cat vào cái `..Hiding-from..` trước thì nó ra luôn passw là `xzTXq1rDJQVVAzdv5cHq1TQytTWufAMq`

<img width="624" height="173" alt="image" src="https://github.com/user-attachments/assets/3c85a899-d184-44f9-a9b4-9171c3a2697c" />

Tò mò không biết `.` và `..` ko biết là thư mục gì, chưa đụng mà đã ra passw, thì thử `cd` vào xem. Nhưng có vẻ không được, tra thông tin thì mới biết `.` đại diện cho thư mục hiện tại còn `..` là lùi về 1 thư mục. 

<img width="651" height="178" alt="image" src="https://github.com/user-attachments/assets/bf0a8154-b34f-4ade-929d-7ee43b25a145" />


















