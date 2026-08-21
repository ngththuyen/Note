<p align="center">
  <img src="https://sb.nordcdn.com/m/0a57c4f40ef76785/webimage-NordVPN-for-Linux-release-notes-svg.jpg" alt="Linux">
</p>

## Giới thiệu
Linux là một hệ điều hành, tương tự như iOS, Windows hoặc Android (OS hay hệ điều hành là phần mềm quản lí các phần cứng của máy tính, tạo sự giao tiếp giữa các ứng dụng với các phần cứng). Linux có rất nhiều bản phân phối phục vụ các nhu cầu khác nhau được gọi là các "distro" như Ubuntu, Debian, Mint,..

## Các thành phần cơ bản của một OS 
**Bootloader:** Một đoạn code chạy để hướng dẫn quá trình khởi động OS khi ta nhấn nút nguồn. Nhiệm vụ của nó là tìm OS ở đâu trên ổ cứng rồi load kernel vào RAM sau đó bàn giao quyền điều khiển cho kernel để kernel khởi động toàn bộ hệ thống. Parrot Linux sử dụng GRUB BootLoader.

Ví dụ: Hình dung Bootloader là đàn em của OS, khi bạn cần tìm gặp đại ca, thì đàn em sẽ tìm đại ca đang ở phòng nào (tìm OS trên disk), đưa đại ca lên phòng làm việc chính (load kernel vào Random Access Memory), rồi im lặng rút lui để đại ca toàn quyền xử lí công việc tiếp theo.

**OS Kernel:** Là thành phần chính của hệ điều hành, là đầu mối duy nhất giao tiếp trực tiếp được với CPU/RAM/Ổ cứng/.. Kernel quyết định được:
- App nào được dùng CPU và dùng trong bao lâu
- Vùng RAM nào được cấp cho app nào (Như 1 vùng RAM cho Chrome, 1 vùng cho Word, Chrome nặng quá tràn ram crash thì ko ảnh hưởng gì tới Word)
- Đọc/ghi dữ liệu nào vào ổ cứng, kết nối mạng ra sao,..

Ví dụ: Khi chạy lệnh `cat file.txt`, lúc này cat phải gửi yêu cầu gọi là system call đến kernel xin phép được đọc file, kernel sau đó sẽ kiểm tra file có tồn tại ko? người dùng có được quyền đọc file này ko?, nếu hợp lệ thì kernel ra lệnh cho ổ cứng đọc dữ liệu rồi trả về cho cat hiện lên màn hình.

**Daemons:** Dịch vụ chạy ở nền (chạy ngầm) được gọi là "daemons" trong Linux. Mục đích của nó là giúp những chức năng như lịch trình, in ấn và đa phương tiện hoạt động ổn định. Những chươn trình này hoạt động sau khi khởi động hoặc đăng nhập vào máy tính

**OS Shell:** Là giao diện dòng lệnh (CLI) cho phép nguời dùng ra lệnh cho hệ điều hành thực hiện các tác vụ. Một số shell phổ biến là Bash, Tcsh/Csh, Ksh,..

**Graphics server:** Cung cấp hệ thống máy chủ đồ hoạ con gọi là "X" hay "X-server" cho phép các chương trình đồ hoạ chạy nội bộ hay từ xa.

**Window Manager:** Hay còn gọi là giao diện đồ hoạ người dùng (GUI). Có rất nhiều loại như GNOME, KDE, MATE, Unity, và Cinnamon. Một môi trường máy tính thường có nhiều ứng dụng, bao gồm trình duyệt tệp và trình duyệt web. GUI cho phép người dùng truy cập và quản lí những tính năng/dịch vụ thiết yếu hay thường xuyên sử dụng trong hệ điều hành

**Utilities:** Là những chương trình thực thi các tác vụ cụ thể cho người dùng hoặc chương trình khác

Kiến trúc Linux
