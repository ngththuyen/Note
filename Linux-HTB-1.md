<p align="center">
  <img src="https://sb.nordcdn.com/m/0a57c4f40ef76785/webimage-NordVPN-for-Linux-release-notes-svg.jpg" alt="Linux">
</p>

## Giới thiệu
Linux là một hệ điều hành, tương tự như iOS, Windows hoặc Android (OS hay hệ điều hành là phần mềm quản lí các phần cứng của máy tính, tạo sự giao tiếp giữa các ứng dụng với các phần cứng). Linux có rất nhiều bản phân phối phục vụ các nhu cầu khác nhau được gọi là các "distro" như Ubuntu, Debian, Mint,..

## Các thành phần cơ bản của Linux
**Bootloader:** Một đoạn code chạy để hướng dẫn quá trình khởi động OS khi ta nhấn nút nguồn. Nhiệm vụ của nó là tìm OS ở đâu trên ổ cứng rồi load kernel vào RAM sau đó bàn giao quyền điều khiển cho kernel để kernel khởi động toàn bộ hệ thống. Parrot Linux sử dụng GRUB BootLoader.

Ví dụ: Hình dung Bootloader là đàn em của OS, khi bạn cần tìm gặp đại ca, thì đàn em sẽ tìm đại ca đang ở phòng nào (tìm OS trên disk), đưa đại ca lên phòng làm việc chính (load kernel vào Random Access Memory), rồi im lặng rút lui để đại ca toàn quyền xử lí công việc tiếp theo.

**OS Kernel:** Là thành phần chính của hệ điều hành, là đầu mối duy nhất giao tiếp trực tiếp được với CPU/RAM/Ổ cứng/.. Kernel quyết định được:
- App nào được dùng CPU và dùng trong bao lâu
- Vùng RAM nào được cấp cho app nào (Như 1 vùng RAM cho Chrome, 1 vùng cho Word, Chrome nặng quá tràn ram crash thì ko ảnh hưởng gì tới Word)
- Đọc/ghi dữ liệu nào vào ổ cứng, kết nối mạng ra sao,..

Ví dụ: Khi chạy lệnh `cat file.txt`, lúc này cat phải gửi yêu cầu gọi là system call đến kernel xin phép được đọc file, kernel sau đó sẽ kiểm tra file có tồn tại ko? người dùng có được quyền đọc file này ko?, nếu hợp lệ thì kernel ra lệnh cho ổ cứng đọc dữ liệu rồi trả về cho cat hiện lên màn hình.

**Daemons:** Dịch vụ chạy ở nền (chạy ngầm) được gọi là "daemons" trong Linux. Mục đích của nó là giúp những chức năng như lịch trình, in ấn và đa phương tiện hoạt động ổn định. Những chương trình này hoạt động sau khi khởi động hoặc đăng nhập vào máy tính, thường có đuôi `d` ở cuối tên.

Ví dụ: `sshd` giúp kết nối ssh từ xa, `crond` quản lí các tác vụ được lên lịch, `cupsd` quản lí máy in, `NetworkManager` quản lí kết nối mạng

**OS Shell:** Là giao diện dòng lệnh (CLI) làm vai trò trung gian giữa người dùng và OS cho phép nguời dùng ra lệnh cho OS thực hiện các tác vụ. Khi ta gửi một dòng lệnh lên thì shell sẽ phân tích lệnh đó, nếu lệnh đó có sẵn trong shell thì tự gọi system call tới kernel luôn còn lệnh thuộc chương trình khác thì shell sẽ tạo một tiến trình mới rồi chuyển sang cho kernel hiểu và thực thi. Một số shell phổ biến là Bash, Tcsh/Csh, Ksh,..

**Graphics Server (X-Server):** Là phần nền tảng chịu trách nhiệm vẽ đồ hoạ lên màn hình, xử lí input từ chuột/bàn phím, cửa sổ, hiển thị hình ảnh,.. Điểm đặc biệt là nó có thể chạy từ xa qua mạng, tức là ta có thể chạy máy chủ đồ hoạ từ xa rồi hiển thị giao diện trên máy tính của ta.

Ví dụ: Khi ta click chuột trong ứng dụng sẽ có quy trình như sau
1. Chuột gửi tín hiệu đến kernel
2. Kernel chuyển tín hiệu đến cho X-Server
3. X-Server tính toán toạ độ chuột (x,y) này đang nằm ở cửa sổ ứng dụng nào?
4. X-Server gửi sự kiện click tại toạ độ (x,y) vào ứng dụng đó
5. Ứng dụng xử lí logic (nút được bấm), rồi trả về yêu cầu cho X-Server là vẽ lại cái nút này được nhấn r
6. X-Server vẽ pixel mới trên màn hình

**Window Manager:** Hay còn gọi là giao diện đồ hoạ người dùng (GUI). Là "bộ mặt" mà ta nhìn thấy hằng ngày như Icon, tab, thu nhỏ, phóng to,.. Có rất nhiều loại như GNOME, KDE, MATE, Unity, và Cinnamon. 

**Utilities:** Là những chương trình nhỏ thực thi các tác vụ cụ thể và có thể kết hợp với nhiều chương trình nhỏ khác để làm việc lớn hơn. Đúng theo triết lý của Unix là "làm một việc và làm thật tốt".

Ví dụ: `cat` để xem nội dung file, `grep` để tìm kiếm văn bản,.. Hình dung nó như một bộ công cụ sửa chữa gồm cờ lê, ốc, tua vít, kìm, búa.. mỗi thằng sẽ có một công dụng khác nhau. Và để tạo ra một sản phẩm tốt thì người thợ cần thuần thục sử dụng các công cụ đó theo đúng công dụng của nó.

## Kiến trúc Linux
**Hardware (Phần cứng):** Là lớp thấp nhất chỉ bao gồm những thiết bị điện tử thuần tuý như RAM, Ổ cứng, CPU,..

**Kernel:** Là lõi của hệ điều hành Linux, là lớp duy nhất có khả năng giao tiếp trực tiếp với phần cứng. Bên cạnh đó kernel còn có khả năng virtualize (ảo hoá) giúp đánh lừa các tiến trình là nó đang sở hữu toàn bộ CPU/RAM của máy dù máy đang mở nhiều tiến trình cùng lúc.

**Shell:** Là giao diện dòng lệnh (CLI), có khả năng đưa các dòng lệnh của người dùng cho kernel hiểu và xử lí.

**System Utility:** Là lớp gần người dùng nhất, cung cấp các chương trình, công cụ chúng ta tương tác hằng ngày ví dụ như trình duyệt, soạn thảo văn bản, ra lệnh,..
 
## Phân cấp tệp tin trong Linux
Linux 
<img width="2576" height="1656" alt="image" src="https://github.com/user-attachments/assets/a83c3e56-4847-437c-8608-f4b19fa8a7ca" />

