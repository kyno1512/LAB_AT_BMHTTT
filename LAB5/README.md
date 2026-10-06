\# LAB 5 - CẤU HÌNH TƯỜNG LỬA PFSENSE



\## 1. Thông tin sinh viên



\- Họ và tên: Ngô Thành Hữu

\- MSSV: 1150070015

\- Lớp: 11TMDT

\- Môn học: An toàn hệ thống thông tin

\- Bài thực hành: Lab 5

linh youtou:https://youtu.be/kKxZ0yukDZ4

\## 2. Nội dung đã thực hiện



Trong Lab 5, em thực hiện xây dựng mô hình mạng và cấu hình tường lửa pfSense trên VMware Workstation.



Các nội dung đã thực hiện:



\- Kiểm tra cấu hình mạng trên máy thật bằng `ipconfig` và `route print`.

\- Tạo và cấu hình máy ảo pfSense.

\- Cấu hình 3 card mạng cho pfSense gồm WAN, LAN và DMZ.

\- Cấu hình WAN sử dụng Bridged.

\- Cấu hình LAN sử dụng mạng `10.0.0.0/8`.

\- Đặt địa chỉ LAN của pfSense là `10.0.0.1/8`.

\- Cấu hình Domain Controller sử dụng địa chỉ IP tĩnh `10.0.0.2/8`.

\- Cấu hình Default Gateway của Domain Controller là `10.0.0.1`.

\- Cài đặt Active Directory Domain Services và DNS Server trên Windows Server.

\- Tạo mạng DMZ sử dụng dải `172.16.0.0/16`.

\- Cấu hình interface DMZ của pfSense với địa chỉ `172.16.0.1/16`.

\- Thực hiện cấu hình NAT và các Firewall Rule theo yêu cầu của bài Lab.

\- Thực hiện các tình huống kiểm thử PASS/FAIL để kiểm tra hoạt động của Firewall.

\- Kiểm tra log của pfSense để xác minh các kết nối được cho phép hoặc bị chặn.



\## 3. Mô hình địa chỉ IP



\- pfSense WAN: Nhận IP từ mạng bên ngoài thông qua Bridged.

\- pfSense LAN: `10.0.0.1/8`.

\- Domain Controller: `10.0.0.2/8`.

\- Gateway LAN: `10.0.0.1`.

\- DNS của Domain Controller: `10.0.0.2`.

\- pfSense DMZ: `172.16.0.1/16`.

\- DMZ-Web: `172.16.0.2/16`.

\- Gateway DMZ-Web: `172.16.0.1`.



\## 4. Kết quả thực hiện



\- Cài đặt và khởi động pfSense thành công.

\- Cấu hình thành công các interface WAN, LAN và DMZ.

\- Máy Domain Controller kết nối được với pfSense qua mạng LAN.

\- Domain Controller ping thành công tới `10.0.0.1`.

\- Cài đặt thành công AD DS và DNS Server.

\- Cấu hình thành công mạng DMZ `172.16.0.0/16`.

\- Cấu hình địa chỉ DMZ của pfSense là `172.16.0.1/16`.

\- NAT và Firewall Rule hoạt động theo các yêu cầu của bài thực hành.

\- Các tình huống kiểm thử PASS/FAIL được thực hiện và lưu lại kết quả.

\- Firewall log được sử dụng để kiểm tra và xác minh lưu lượng mạng.



\## 5. Lỗi gặp phải và cách khắc phục



\- pfSense ban đầu chỉ nhận một card mạng.

&#x20; - Khắc phục: Tắt máy ảo và thêm đủ 3 Network Adapter cho WAN, LAN và DMZ.



\- VMnet bị cấu hình sai hoặc chồng lấn dải mạng.

&#x20; - Khắc phục: Cấu hình lại VMnet1 cho LAN `10.0.0.0/8` và VMnet2 cho DMZ `172.16.0.0/16`.



\- Không truy cập được WebGUI pfSense.

&#x20; - Khắc phục: Kiểm tra kết nối LAN, ping `10.0.0.1` và restart WebConfigurator trên pfSense.



\- Trình duyệt cảnh báo chứng chỉ khi truy cập pfSense.

&#x20; - Khắc phục: Xác nhận tiếp tục truy cập do pfSense sử dụng chứng chỉ HTTPS tự ký trong môi trường Lab.



\## 6. Kết luận



Qua Lab 5, em đã thực hành triển khai pfSense trên môi trường VMware, cấu hình các vùng mạng WAN, LAN và DMZ, thiết lập NAT và Firewall Rule, đồng thời kiểm tra hoạt động của các chính sách tường lửa thông qua các tình huống kiểm thử và firewall log.

