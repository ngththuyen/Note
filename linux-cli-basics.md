> 18/08/26 - Viết bằng tay, chỉ dùng AI để tìm hiểu khái niệm
## Terminal là gì?
Terminal là giao diện thao tác dựa vào các dòng lệnh (Command Line Interface) thay vì tương tác trực tiếp với các đồ hoạ. Nhiều chuyên gia trong lĩnh vực cybersec ưu tiên sử dụng nó vì:
- Thao tác nhanh hơn so với việc nhấp chuột
- Có nhiều quyền điều khiển hơn
- Nhiều tool mạnh chỉ chạy trên terminal

## Các lệnh Linux CLI cơ bản:
- `pwd`: in ra thư mục hiện tại Terminal đang ở (Print Working Directory)

Ví dụ: 
```bash
root@ngththuyen:~$ pwd
/home/ubuntu
```
- `ls`: in ra trong thư mục đang ở chứa những tệp và thư mục gì. Bên cạnh đó ta có thêm tham số như:
  + `-l` để hiển thị nhiều thông tin chi tiết hơn 
  + `-a` để hiển thị thêm cả các file ẩn như file hệ thống, config,..
Ví dụ: 
```bash
root@ngththuyen:~$ ls
documents/  projects/
root@ngththuyen:~$ ls -l
total 8
drwxr-xr-x   2  user  user   4096  Aug 18 20:45  documents/
drwxr-xr-x   2  user  user   4096  Aug 18 20:45  projects/
root@ngththuyen:~$ ls -a
./  ../  .gitconfig  .zshrc  documents/  projects/
```
- `cd <đích>`: di chuyển từ folder hiện tại đến folder <đích>

Ví dụ: 
```bash
root@ngththuyen:~$ cd documents
root@ngththuyen:~/documents$
root@ngththuyen:~/documents$ cd ..
root@ngththuyen:~$
```

- `cat <file>`: đọc nội dung của <file> trên terminal
- `whoami`: xem tên đăng nhập hiện tại
- `uname -a`: xem tên OS, phiên bản kernal,.. hiện tại đang dùng
- `man <lệnh>`: tra cứu tài liệu hướng dẫn của <lệnh>
- `df -h`: để xem dung lượng của hệ thống hiện tại còn bao nhiêu, dùng bao nhiêu, % sử dụng. Tham số `-h` là human readable

