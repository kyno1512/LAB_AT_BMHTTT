**BÁO CÁO THỰC HÀNH LAB 3: NHẬN DIỆN VÀ ỨNG PHÓ CÁC MỐI ĐE DỌA ATTT**

**Môn học: An toàn và Bảo mật Hệ thống Thông tin**

**Họ và tên: Ngô Thành Hữu**

**MSSV: 1150070015**

**Lớp: 11TMĐT**

**Link YouTube: https://www.youtube.com/watch?v=PSNQwLUHkY4**

1\. Môi trường thực hành



Sử dụng máy ảo Windows 11 trên VMware, cấu hình mạng Host-only, kiểm tra phiên bản bằng winver và chuẩn bị môi trường LAB3.



2\. Baseline



Kiểm tra Microsoft Defender và Windows Firewall trước khi thực hành.



Kết quả:



Defender hoạt động

RealTimeProtectionEnabled = True

Domain, Private, Public Firewall đều bật

Đã lưu cấu hình mạng và danh sách tiến trình vào C:\\LAB3\\Evidence



Ảnh H3: Defender + Firewall.



3\. Tình huống 1 – Risk Register



Xác định mối quan hệ:



Asset → Vulnerability → Threat → Risk → Control



Các nhóm nguy cơ gồm hành động vô ý, cố ý, sự cố môi trường, lỗi kỹ thuật và lỗi quản lý.



4\. Tình huống 2 – EICAR



Tạo mẫu kiểm thử EICAR để kiểm tra Microsoft Defender.



Kết quả:



Defender phát hiện EICAR

ActionSuccess = True

Defender vẫn bật bảo vệ thời gian thực



Ảnh H4: Protection History có EICAR.



5\. Tình huống 3 – Đăng nhập sai



Tạo tài khoản lab3user, bật Audit Logon và thực hiện thử đăng nhập sai.



Kết quả: Windows ghi nhận sự kiện đăng nhập thất bại.



Ảnh H5: Event Viewer – Event ID 4625 của lab3user.



6\. Tình huống 4 – Persistence và Listener



Cài Sysmon và ghi nhận Event ID 1 – Process Create.



Tạo Run Key:



LAB3\_Run\_Demo → notepad.exe



Autoruns phát hiện mục persistence này trong tab Logon.



Sau đó chạy HTTP server:



127.0.0.1:8080



và dùng Process Explorer xác nhận tiến trình python.exe sở hữu cổng 8080.



H6: Sysmon Event ID 1

H7: Autoruns LAB3\_Run\_Demo

H8: Process Explorer python.exe + PID

7\. Kết luận



Qua các tình huống thực hành, có thể sử dụng Microsoft Defender, Event Viewer, Sysmon, Autoruns và Process Explorer để nhận diện các dấu hiệu bất thường, persistence, đăng nhập thất bại và tiến trình đang lắng nghe trên hệ thống.

