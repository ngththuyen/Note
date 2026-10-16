# OverTheWire: Bandit
## Lvl 0
Đề yêu cầu phải tìm hiểu về SSH để kết nối vào host có Domain là `bandit.labs.overthewire.org` và Port là `2220`, username là `bandit0` và passw là `bandit0`. Bài này ta dùng lệnh SSH với pháp cơ bản là `ssh <username>@<domain> -p <port>`.

<img width="716" height="336" alt="image" src="https://github.com/user-attachments/assets/1ecfe8b7-eac9-48a8-b2ac-7fdb488cb1e2" />

Sau khi dùng lệnh thì nó sẽ yêu cầu điền mật khẩu, ta điền đúng với mk đề đã cấp thì sẽ truy cập được 

<img width="875" height="494" alt="image" src="https://github.com/user-attachments/assets/4d59e4a6-a4c2-440d-b803-077664e0fe62" />

## Lvl 0-1
Mục tiêu của bài này là tìm được file `readme` ở thư mục `home`, trong đó sẽ có passw để SSH vào bài tiếp theo. Ta dùng lệnh `pwd` để kiểm tra hiện tại đang đứng ở đâu thì nó trả về `home/bandit0`, thử dùng `ls` thì thấy được là trong nơi ta đang đứng có chứa file tên `readme`.

<img width="405" height="147" alt="image" src="https://github.com/user-attachments/assets/d0fc89e1-bc77-4d11-a9be-53e0955f16b6" />

Ta dùng lệnh `cat` để đọc file đó thì thu được passw cho màn tiếp theo là `6y2kwnwK6grgvwvpvLaa2T1cpFEKOhNR`. 

<img width="898" height="264" alt="image" src="https://github.com/user-attachments/assets/f75431b4-34aa-414a-86d1-202abae694d3" />

## Lvl 1-2
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

## Lvl 3-4
Bài này thì nó bảo là passw nằm ở trong 1 file ẩn ở trong thư mục `inhere`, dùng `ls` ở vị trí hiện tại thì thấy 1 folder `inhere`. Ta `cd` vào rồi dùng `ls` tiếp thì ko thấy bất cứ thứ gì như đề bảo thật, file passw đã bị ẩn.

<img width="450" height="174" alt="image" src="https://github.com/user-attachments/assets/1fccfd84-f9ba-456c-b895-a5a1b7f4434b" />

Ta dùng lệnh `ls --help` xem có option gì khác để check không thì thấy có tham số `-a` là sẽ có tác dụng ko bỏ qua file bị ẩn.

<img width="1329" height="444" alt="image" src="https://github.com/user-attachments/assets/209e039e-2a50-4be2-87f7-cd6b0d5e616d" />

Dùng `ls -a` thì đúng thật là xuất hiện thêm các folder/file khác. Thử cat vào cái `..Hiding-from..` trước thì nó ra luôn passw là `xzTXq1rDJQVVAzdv5cHq1TQytTWufAMq`

<img width="624" height="173" alt="image" src="https://github.com/user-attachments/assets/3c85a899-d184-44f9-a9b4-9171c3a2697c" />

Tò mò không biết `.` và `..` ko biết là thư mục gì, chưa đụng mà đã ra passw, thì thử `cd` vào xem. Nhưng có vẻ không được, tra thông tin thì mới biết `.` đại diện cho thư mục hiện tại còn `..` là lùi về 1 thư mục. 

<img width="651" height="178" alt="image" src="https://github.com/user-attachments/assets/bf0a8154-b34f-4ade-929d-7ee43b25a145" />

## Lvl 4-5
Đến bài này thì nó kêu là file passw nằm trong 1 file mà chỉ con người đọc được và ở trong folder `inhere`. Trước hết thì `cd` vào folder đó trước rồi `ls` xem có những file nào thì nó hiện tầm 10 file.

<img width="917" height="133" alt="image" src="https://github.com/user-attachments/assets/cff58a37-77d7-432d-8216-166d43e5b22b" />

Trông thế này chắc đi check từng file để tìm passw, ngồi dò một hồi thì tới file thứ 8 nó mới ra passw là `6C7h9GD8M6ai5nr7wo1RonrzFjj9yIrG`

<img width="1076" height="575" alt="image" src="https://github.com/user-attachments/assets/a1bccd24-2f39-4783-a768-0d03e240d767" />

## Lvl 5-6
Lần này thì đề bảo passw nằm trong file thuọc folder `inhere` với các thuộc tính "human-readable ,1033 bytes in size, not executable". Thử dùng `ls` thì nó cho quả tầm 20 folder

<img width="1344" height="207" alt="image" src="https://github.com/user-attachments/assets/39a7acd8-4fd0-44d2-9f50-af18131a7c87" />

Thử vào 1 folder xem bên trong ntn thì trong nó chứa thêm mớ file nữa, có vẻ ngồi duyệt từng thằng khá khoai.

<img width="749" height="176" alt="image" src="https://github.com/user-attachments/assets/d082eec5-1ebe-4c73-8909-f8e389671401" />

Tra thông tin trên mạng thì có lệnh `find` hỗ trợ tìm được file có kích thước cụ thể, như dữ kiện là 1033 byte và đọc được thì ta dùng lệnh `find -readable -size 1033c` từ đó cho ra vị trí là `./maybehere07/.file2`. Tại sao 1033 byte lại ghi là 1033c thì do c ở đây là viết tắc của character tức ký tự, trong OS Linux thì nó quy định 1 ký tự = 1 byte

<img width="1099" height="296" alt="image" src="https://github.com/user-attachments/assets/0b339b00-81fd-4fc3-802e-13c48b9323a6" />

## Lvl 6-7
Bài này thì để nó bảo là passw nằm trong file nào đó ở trong server với thuộc tính "owned by user bandit7, owned by group bandit6, 33 bytes in size". Tức bài này ta có vẻ phải dùng `find` ở phạm vi rộng hơn, thử dùng `ls` lại vị trí hiện tại thì ko thấy file nào.

<img width="573" height="203" alt="image" src="https://github.com/user-attachments/assets/d33c6146-5c28-4def-966e-12e0bce08391" />

Thử `cd ..` để lùi về 1 vị trí thì thấy 1 mớ folder gì đấy

<img width="1347" height="362" alt="image" src="https://github.com/user-attachments/assets/96eb0cb9-f3d2-41be-8429-d3dcbf0e0cd7" />

2 cái dữ kiện kia thì chưa biết như thế nào, nhưng mà có cái 33byte thì thử đứng ở folder `home` này rồi dùng `find -size 33c` xem sao. Tìm thì đúng là ra một đống file nhma toàn của bài khác và ko có quyền truy cập, có vẻ ta phải về đúng thư mục của mình rồi xử lí tiếp

<img width="957" height="563" alt="image" src="https://github.com/user-attachments/assets/04562c93-5920-4e6e-9ca6-30c98b5a3675" />

Mà về thư mục bài của mình thì ko có file nào mới đau đầu, tìm cũng k ra, thử `ls -a` thì có ra một số file lạ khác. Thử cat mấy file đó mà toàn ra gì đâu, có vẻ không đúng file passw rồi. Giờ muốn giải phải tập trung vào dữ kiện owner by user và group

<img width="894" height="560" alt="image" src="https://github.com/user-attachments/assets/7fefc041-3011-4160-b355-52c5237c2958" />

Tra mạng thì có tham số là `-user` và `-owner` cho find, thử find trong folder bài hiện tại thì ko được, thử `cd ..` về thư mục gốc của server rồi dùng `find` thì ra mớ bùi nhùi như bên dưới.

<img width="1026" height="587" alt="image" src="https://github.com/user-attachments/assets/7e4a7b0d-b60b-45fa-b9c6-b861742d6af3" />

Căng mắt ra dò thì thấy ở dưới cùng có 1 file ko bị permission deni với đường dẫn là `./var/lib/dpkg/info/bandit7.password`, cat vào thì ra passw là `Bmnnvf82KzQlfxgAI2d1zYbr1u9pr3E3`

<img width="948" height="448" alt="image" src="https://github.com/user-attachments/assets/064ae07d-4db0-4110-bfa1-926210858efb" />

## Lvl 7-8
"The password for the next level is stored in the file data.txt next to the word millionth". Bài này có 1 file data.txt, thử cat thì bên trong nó có 1 mớ nội dung load mãi không hết, có vẻ phải dùng lệnh để tìm ở bên ngoài. 

<img width="686" height="514" alt="image" src="https://github.com/user-attachments/assets/0fd118bb-458e-4b8e-8af7-98a7554a1add" />

Theo hint của overthewire thì ta sẽ phải tìm hiểu lệnh `grep`, lânhj này có tác dụng tìm kiếm chuỗi kí tự trong file ta đưa cho nó.

<img width="710" height="614" alt="image" src="https://github.com/user-attachments/assets/e12016f4-86f0-4e1b-9c30-dee358120981" />

Đọc qua hướng dẫn, dùng `grep 'millionth' data.txt` thì ra luôn passw là `VR1ljMayciFxbnUokuQmJFw6QC9VKtub`

<img width="485" height="125" alt="image" src="https://github.com/user-attachments/assets/7c690da3-2259-4bcc-ba13-6fd1cb10546c" />

## Lvl 8-9
"The password for the next level is stored in the file data.txt and is the only line of text that occurs only once". Tương tự cũng là tìm chuỗi kí tự trong 1 mớ hỗn độn nhưng lần này đề yêu cầu là tìm dòng kí tự nào chỉ xuất hiện 1 lần. Thử cat file data.txt xem qua nó như thế nào thì nó là file chứa hàng loạt dãy kí tự có độ dài như nhau.

<img width="515" height="557" alt="image" src="https://github.com/user-attachments/assets/c81ce99d-d698-40a8-a2cf-95b74fb48db9" />

Trong hint của web bài tập thì có ghi 1 lệnh là `uniq` có vẻ là viết tắt của từ `unique` mang nghĩa độc nhất. Thử check hd của lệnh này thì đúng như dự đoán

<img width="1357" height="400" alt="image" src="https://github.com/user-attachments/assets/0dd1a12e-8102-4ca4-bf28-153ec8e0fa00" />

Thử dùng lệnh `uniq data.txt` thì có vẻ ko có tác dụng, nó cũng in mớ lộn xộn đó, chắc là sai cú pháp nào đó

<img width="860" height="616" alt="image" src="https://github.com/user-attachments/assets/55233f67-a2d4-4ebd-b204-7dacd37d3685" />

Ngồi mò một hồi thì mới biết có cả vụ này, chắc do đọc không kỹ hướng dẫn của lệnh. 

<img width="735" height="298" alt="image" src="https://github.com/user-attachments/assets/fef61e24-8399-4533-a5cb-28433fe15868" />

Ta thử lại với lệnh sort, sau đó kết hợp toán tử `|` (pipeline) trong Linux để lấy ouput của lệnh phía trước gắn vào lệnh phía sau từ đó ra passw unique là `EjmOSvuAu7sGAHqHVcBDPirRe9T03kxl`. Lưu ý là thằng `uniq` phải thêm tham số `-u` nó mới in cho mình cái độc nhất, chứ nếu ko thêm thì nó sẽ in thêm mấy cái từng lặp lại nhưng bị xoá còn 1 cái. VD như "A A B C C" thì ko có `-u` là nó in "A B C" còn có thì nó sẽ in "B" thôi, vì đề bài cần tìm cái xuất hiện 1 lần nên phải dùng nó.

<img width="1334" height="532" alt="image" src="https://github.com/user-attachments/assets/74211d9f-776f-4c5b-93e6-a7048e42377c" />

## Lvl 9-10
"The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.". Passw là 1 vài kí tự con người đọc đc, đứng sau mấy dấu =. Thử cat thì đúng là ra mớ bùi nhùi thật nhưng mà có vẻ file hơi ngắn nên nhìn xíu là thấy luôn đáp án là `B0s2khmbT9u0geKuOoVGW3JZKhndE3BG`. Không biết bài này họ hướng dẫn dùng tool gì nhưng lỡ ra đáp án rồi nên thôi cho qua.

<img width="1366" height="658" alt="image" src="https://github.com/user-attachments/assets/1d53be0f-808a-4212-b6da-7541be025dc5" />

## Lvl 10-11
"The password for the next level is stored in the file data.txt, which contains base64 encoded data". Passw được mã hoá dạng base64, thử cat thì đúng là 1 dòng nội dung bị mã hoá

<img width="650" height="132" alt="image" src="https://github.com/user-attachments/assets/43b79248-dd42-46b9-9010-0b8ffbd92142" />

Bài này đơn giản là search google tìm web decode thôi, những vấn đề này mò lệnh Linux lại tốn thời gian mà sợ cũng không đụng nhiều lệnh đó bằng việc search. 

<img width="868" height="515" alt="image" src="https://github.com/user-attachments/assets/b7f932d8-7114-4b2a-b3a0-4b54d40e2ba4" />

Kết quả decode thu được "The password is `pYfOY6HwUsDj5rL9UvyhU7MCmv8vN5Ro`"

## Lvl 11-12
"The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions". Bài này đọc đề ko hiểu lắm, a-z và A-Z bị xoay 13 vị trí là sao. Thử cat file xem ntn

<img width="539" height="143" alt="image" src="https://github.com/user-attachments/assets/c47ed0df-daef-490c-82c1-42a086e68573" />

Nếu như ý để ở đây là trong bảng mã ascii nó bị +- 13 đơn vị thì ta phải chuyển lại. Nhìn nội dung file ngồi đếm số kí tự từng từ thì biết ngay 3 từ đầu là "The password is" rồi. Mà để kí từ G biến thành T thì theo bảng mã là +13 đơn vị thật. Tức để giải bài này ta cần duyệt từng từ rồi cộng từng kí tự lên 13 đơn vị. Thử viết code C++ rồi cộng các kí tự lên 13 thì có vẻ là gần ra, bài này ko như suy đoán ban đầu là +13 mà nó còn có trường hợp -13.

<img width="1250" height="491" alt="image" src="https://github.com/user-attachments/assets/4a972fb9-93dd-4373-abba-86771c491d47" />

Thử dùng 2 biến để lưu 2 trường hợp rồi xuất ra và đối chiếu, ngồi dò quy luật

<img width="1194" height="420" alt="image" src="https://github.com/user-attachments/assets/b3aa485b-9e4d-4d8c-acfb-ce9c7e2e23fd" />

Ngồi suy luận một hồi dựa vào những manh mối từ các passw của các bài trước đó để loại trừ thì ta có thể kết luận là kí tự mà hợp lệ thì nó 1 là nằm ở +13 2 là nằm ở -13 chứ ko thể nằm ở cả 2 chuỗi. VD như kí tự `Y` đi, nó xuất hiện ở chuỗi 1 tại vị trí gần cuối vì ở vị trí đó chuỗi 2 nó là kí tự ? (Chưa bao giờ xuất hiện ở passw các bài trước), còn ở chuỗi 2 thì thằng `Y` nó bị thay bởi mấy thằng như `s`,`i` do dữ liệu 3 từ đầu phải là The password is.

<img width="499" height="112" alt="image" src="https://github.com/user-attachments/assets/f3dac993-1083-4824-a692-d1c06426e9e4" />

Tiếp tục ngồi loại trừ, rồi lại rơi vào bế tắc, có vị trí cả 2 chuỗi đều là kí tự đặc biệt 😩

<img width="499" height="112" alt="image" src="https://github.com/user-attachments/assets/1e71ec53-6142-4641-8327-6aa9aa781774" />

Bí, ngồi đọc lại đề thì nó có link dẫn tới wiki của ROT13, có vẻ bài này dùng kĩ thuật mã hoá chứ ko đơn giản ngồi cộng trừ như suy đoán. Nếu như vậy thì ta lên web decode rot13 thôi, ra passw là `GROozWPO8QyN0mGrjUkID0WCYkZiQxrN`

<img width="1196" height="575" alt="image" src="https://github.com/user-attachments/assets/d01397d0-7dc7-4782-9c7c-91caf60329a7" />

## Lvl 12-13
"The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)" 

Thử cat file thì nó ra cái đống lộn xộn gì đây @@

<img width="725" height="678" alt="image" src="https://github.com/user-attachments/assets/81873ae0-0545-4351-8a75-eeb88ed4fe50" />

Đề bảo là "which is a hexdump of a file that has been repeatedly compressed", có vẻ cần phải tìm hiểu phạm vi kiến thức này

<img width="1220" height="702" alt="image" src="https://github.com/user-attachments/assets/0ef82b53-ddef-4890-a437-8588dee4136f" />

Bài này hơi lòng vòng với cả cũng không quá liên quan tới mảng web vì đây có phần mã máy nên chắc sẽ sơ lược cách giải, sau khi tra thông tin một hổi từ các nguồn cụ thể là AI thì ý bài này là cho 1 tệp nó bị nén qua nhiều lớp định dạng, cài file data.txt ban đầu là nó là mã máy, nó hint là tên file đó chính xác là data2.bin thì mình phải tạo tên file chứa nội dung tương tự rồi kiểm tra định dạng file đó là gì, cái data2.bin thì dugnf lệnh `file` nó check ra là nó thuộc định dạng gzip, biết rồi thì ta đổi tên thành data2.gz rồi unzip, xogn unzip ra lại tới data3,4,5,6... cứ mỗi lần là 1 thằng định dạng khác nhau như tar,bz nhưng cách thức giải vẫn kiểu vậy, kiểm tra định dạng rồi đổi tên file đúng định dạng rồi unzip cho tới khi ra passw là `qQYQiHOBPR8zR61qxYqX45quvihF2uzk`














































