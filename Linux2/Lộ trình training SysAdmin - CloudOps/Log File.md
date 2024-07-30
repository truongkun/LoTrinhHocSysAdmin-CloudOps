# Tổng quan

Trong hệ thống Linux, các tệp `log` thường được lưu trữ trong thư mục `/var/log`. Dưới đây là mô tả về các file log thường gặp trong hệ thống Linux:


## Khái niệm

Log file là một `tập tin ghi lại các sự kiện, hoạt động hoặc thông tin quan trọng xảy ra trong hệ thống hoặc ứng dụng.`

### Các file log chính của hệ thống:

1. **/var/log/messages**:
   - Lưu trữ các thông điệp từ các chương trình hệ thống và các dịch vụ.
   - Thường là nơi chứa thông tin quan trọng về hoạt động của hệ thống.

2. **/var/log/syslog**:
   - Chứa thông điệp từ hệ thống, nhưng có cấu trúc và bổ sung thêm thông tin định dạng.
   - Thường được sử dụng bởi các phiên bản mới hơn của các bản phân phối Linux.

3. **/var/log/auth.log**:
   - Lưu trữ các thông tin liên quan đến xác thực và các sự kiện bảo mật.
   - Bao gồm các thông báo đăng nhập, thay đổi mật khẩu, hoạt động sudo, vv.

4. **/var/log/kern.log**:
   - Chứa các thông điệp từ nhân hệ điều hành (kernel).
   - Ghi lại các thông tin liên quan đến hoạt động của kernel, lỗi và cảnh báo.

5. **/var/log/boot.log**:
   - Lưu trữ thông tin về quá trình khởi động của hệ thống.
   - Bao gồm các thông tin về quá trình boot, các dịch vụ được khởi động, vv.

6. **/var/log/dmesg**:
   - Là tệp log đầu tiên được tạo ra sau khi khởi động hệ thống.
   - Chứa thông tin về các sự kiện từ kernel trong quá trình khởi động.

7. **/var/log/lastlog**:
   - Ghi lại thông tin về lần đăng nhập cuối cùng của mỗi người dùng.

8. **/var/log/cron**:
   - Lưu trữ các thông tin liên quan đến việc thực thi các tác vụ được lập lịch bởi cron.

9. **/var/log/mail.log**:
   - Lưu trữ các thông tin liên quan đến gửi và nhận email trên hệ thống.

10. **/var/log/secure**:
    - Chứa các thông điệp liên quan đến bảo mật như đăng nhập, sử dụng sudo, vv.

Các tệp log khác cũng có thể tồn tại trong thư mục `/var/log`, tùy thuộc vào cài đặt cụ thể của hệ thống và các dịch vụ được cài đặt.