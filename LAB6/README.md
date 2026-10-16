\# LAB 6 - XÁC THỰC ACTIVE DIRECTORY VÀ CHÍNH SÁCH TRUY CẬP TRÊN pfSense



\## Thông tin sinh viên



\- \*\*Họ và tên:\*\* Ngô Thành Hữu

\- \*\*Mã số sinh viên:\*\* 1150070015

\- \*\*Lớp:\*\* 11TMDT

\- \*\*Môn học:\*\* An toàn hệ thống thông tin

\-link youtobe: https://www.youtube.com/watch?v=YAmrbIaCcW4



\## Tên bài Lab



\*\*LAB 6 - Xác thực Active Directory và chính sách truy cập trên pfSense\*\*



\## Nội dung đã thực hiện



Trong LAB 6, em đã thực hiện các nội dung chính sau:



\- Xây dựng mô hình mạng riêng cho LAB 6 gồm 4 vùng: WAN, MGMT, LAN và DMZ.

\- Cấu hình pfSense với 4 card mạng tương ứng.

\- Cài đặt và cấu hình Domain Controller, Active Directory Domain Services và DNS.

\- Tạo domain `lab6.test`.

\- Tạo các tài khoản người dùng `sv\_a`, `sv\_b` và tài khoản dịch vụ `svc\_pfsense\_ldap`.

\- Tích hợp Active Directory vào pfSense thông qua LDAP.

\- Kiểm tra xác thực tài khoản Active Directory trên pfSense.

\- Cấu hình Captive Portal trên mạng LAN sử dụng Active Directory làm nguồn xác thực.

\- Tạo các Alias cho Client và các website mô phỏng trong vùng DMZ.

\- Tạo Schedule để áp dụng chính sách truy cập theo thời gian.

\- Cấu hình các Firewall Rule theo từng kịch bản:

&#x20; - Chặn Client-A truy cập JOB\_SITE.

&#x20; - Chặn Client-A và Client-B truy cập RESTRICTED\_SITE.

&#x20; - Chỉ cho phép Client-B truy cập SOCIAL\_SITE trong giờ nghỉ.

&#x20; - Giới hạn HTTP/HTTPS trong giờ hành chính.

&#x20; - Cô lập DMZ khỏi LAN.

\- Kiểm tra Firewall Log và State Table.

\- Thực hiện xử lý sự cố liên quan đến LDAP, Captive Portal, Firewall Rule và Schedule.



\## Kết quả thực hiện



\- Xây dựng được mô hình LAB 6 với các vùng WAN, MGMT, LAN và DMZ.

\- pfSense kết nối và xác thực được người dùng từ Active Directory thông qua LDAP.

\- Captive Portal sử dụng tài khoản domain để đăng nhập.

\- Các Alias và Schedule được cấu hình để phục vụ việc xây dựng chính sách truy cập.

\- Các Firewall Rule được triển khai theo từng kịch bản của bài thực hành.

\- Có thể kiểm tra hoạt động của firewall thông qua Firewall Log và State Table.

\- Hiểu được cách pfSense xử lý rule theo cơ chế first-match và stateful firewall.

\- Hiểu được cách kết hợp Active Directory, LDAP, Captive Portal và Firewall Policy trong việc kiểm soát truy cập mạng.
