# LAB 8 (LAB 9): LOCAL DNS ATTACK - DNS SPOOFING VÀ CACHE POISONING

## 1. Thông tin sinh viên
- **Họ và tên sinh viên:** Ngô Thành Hữu
- **Mã số sinh viên:** 1150070015
- **Lớp:** 11TMDT
- **link youtobe:**  https://youtu.be/QLFU4s_yh-Y

## 2. Nội dung đã thực hiện
1. **Dựng mạng DNS-LAB cô lập và cấu hình BIND9:**
   - Thiết lập interface `DNSLAB` (`10.9.0.1/24`) và cấu hình Firewall Rules cô lập trên pfSense.
   - Cài đặt và cấu hình `DNS-SERVER` (`10.9.0.10`) chạy BIND9 đóng vai trò authoritative cho zone `lab9.test` và recursive/caching resolver cho mạng `10.9.0.0/24`.
2. **Kiểm tra Baseline và bắt gói tin DNS:**
   - Khởi động authoritative DNS mô phỏng trên `APP-TEST` (`172.16.6.20:53`) và kiểm tra phân giải `www.external.lab9.test` qua `DNS-SERVER`, quan sát luồng gói tin bằng Wireshark.
3. **Thực hiện 3 kịch bản thử nghiệm:**
   - **Task 1 (Thay đổi file `/etc/hosts`):** Chỉnh sửa cục bộ file `/etc/hosts` trỏ `www.lab9.test` về `10.9.0.200`, kiểm chứng sự khác biệt giữa cơ chế NSS (`getent`, `curl`) và truy vấn DNS trực tiếp (`dig`).
   - **Task 2 (Direct DNS Spoofing):** Chạy script giả mạo ở chế độ `victim` trên Kali (`10.9.0.200`) để gửi phản hồi DNS giả trực tiếp về máy trạm và phân tích gói tin trên Wireshark.
   - **Task 3 (DNS Cache Poisoning):** Chạy script ở chế độ `resolver`, quan sát truy vấn từ `DNS-SERVER` tới `172.16.6.20`, kiểm tra bản dump cache của BIND9 (`named_dump.db`) kèm giá trị TTL.
4. **Khôi phục môi trường và phân tích phòng thủ:**
   - Dừng các dịch vụ mô phỏng, khôi phục `/etc/hosts`, làm sạch cache BIND9 (`rndc flush`) và đánh giá các biện pháp hardening (phân đoạn mạng, DNS COOKIE, DNSSEC, kiểm soát DNS egress).

## 3. Kết quả thực hiện
- **Baseline:** Hệ thống phân giải chính xác `www.external.lab9.test` về IP hợp lệ `172.16.6.10`; Wireshark ghi nhận đầy đủ cặp gói truy vấn và phản hồi chuẩn.
- **Task 1:** Các ứng dụng dùng bộ phân giải hệ điều hành (`getent`, `curl`) bị chuyển hướng sang trang web mô phỏng trên Kali (`10.9.0.200`), trong khi `dig @10.9.0.10` vẫn trả về IP gốc `172.16.6.10`.
- **Task 2 & Task 3:** Quan sát rõ trên Wireshark quá trình cạnh tranh (race condition) giữa phản hồi giả mạo và phản hồi hợp lệ dựa trên việc khớp `Transaction ID`, cổng UDP và cơ chế kiểm tra DNS COOKIE/switch ảo; kiểm tra thành công dữ liệu lưu trong cache BIND9 cùng thời gian sống TTL giảm dần.
- **Khôi phục:** Sau khi xóa cache và khôi phục cấu hình, toàn bộ truy vấn DNS trở lại trạng thái hợp lệ ban đầu (`172.16.6.10`).