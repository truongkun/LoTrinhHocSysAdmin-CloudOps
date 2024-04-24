# File log là gì?

- File log là các tệp tin được sử dụng để ghi lại các sự kiện và hoạt động của hệ thống. 
- Các file log thường được sử dụng trong các ứng dụng và hệ thống máy tính để ghi lại thông tin quan trọng như: lỗi, cảnh báo, thông tin gỡ lỗi, và các hoạt động khác.

## Các file log chứa ở đâu?

- Các file log chứa ở trong var/log.

  - `syslog:` Đây là file log chính của hệ thống, ghi lại thông tin về các hoạt động của hệ thống và các ứng dụng.
  - `auth.log:` Ghi lại các thông tin liên quan đến quá trình xác thực và xác định danh tính, như đăng nhập và đăng xuất của người dùng, cũng như các hoạt động liên quan đến hệ thống xác thực.
  - `kern.log:` Lưu trữ các thông tin liên quan đến kernel, bao gồm các thông báo lỗi và cảnh báo từ kernel.
  - `boot.log:` Ghi lại các thông tin về quá trình khởi động của hệ thống, các dịch vụ.
  - `messages:` File log tổng hợp các thông điệp từ các ứng dụng và dịch vụ khác nhau trên hệ thống.
  - `secure:` Ghi lại các thông tin liên quan đến bảo mật như đăng nhập thành công, thất bại, thay đổi mật khẩu, v.v.

# Rotate log là gì? 

- `Rotate Log` là quá trình chia nhỏ và xoay vòng các file log để đảm bảo rằng chúng không trở nên quá lớn và gây ra các vấn đề về tài nguyên hoặc hiệu suất của hệ thống. 
- Việc này thường được thực hiện để giữ cho các file log ở mức kích thước hợp lý và dễ quản lý.

Có một số cách để thực hiện Rotate Log, một trong những phương pháp phổ biến là:

- `Kích hoạt Rotate Log theo thời gian:` Trong cài đặt này, các file log sẽ được chia nhỏ và xoay vòng dựa trên khoảng thời gian nhất định, chẳng hạn như hàng ngày, hàng tuần hoặc hàng tháng.
- `Kích hoạt Rotate Log theo kích thước file:` Trong cài đặt này, các file log sẽ được chia nhỏ và xoay vòng khi kích thước của chúng vượt quá một ngưỡng cụ thể.
- `Kết hợp Rotate Log theo thời gian và kích thước file:` Một số hệ thống cho phép kích hoạt Rotate Log dựa trên cả hai yếu tố thời gian và kích thước file, đảm bảo rằng các file log không chỉ được xoay vòng định kỳ mà còn được giữ ở kích thước hợp lý.

## Tại sao Rotate Log cần thiết?

- `Quản lý tài nguyên:` Các file log có thể trở nên rất lớn nếu không được quản lý, điều này có thể làm đầy chỗ lưu trữ của hệ thống và gây ra các vấn đề về tài nguyên.
- `Hiệu suất:` Khi các file log trở nên quá lớn, việc mở và xử lý chúng có thể trở nên chậm chạp, ảnh hưởng đến hiệu suất của ứng dụng và hệ thống.
- `Dễ dàng quản lý:` Rotate Log giúp quản trị viên dễ dàng tìm kiếm và phân tích thông tin trong các file log, bằng cách giữ chúng ở kích thước nhỏ và tổ chức cấu trúc hợp lý.

## Cấu hình rotate log cho /var/log/syslog (hiểu các tham số cấu hình.)

- Để cấu hình Rotate Log cho file `/var/log/syslog` trên hệ thống Linux, bạn có thể sử dụng công cụ Rotate Log phổ biến như `logrotate`. Dưới đây là một ví dụ cấu hình cơ bản cho `/var/log/syslog` bằng cách sử dụng `logrotate`:

1. Mở tệp cấu hình `logrotate`:

```
sudo nano /etc/logrotate.d/syslog
```

2. Thêm cấu hình cho `/var/log/syslog` vào tệp:

```
/var/log/syslog {
    rotate 7   # Số lượng bản sao tối đa được giữ lại (ở đây là 7 bản sao)
    daily      # Quay vòng hàng ngày "weely": tuần, "monthly":tháng
    missingok           # Bỏ qua nếu không tìm thấy tệp nhật ký
    notifempty          # Không quay vòng nếu tệp nhật ký rỗng
    delaycompress       # Nén bản sao sau khi quay vòng
    compress            # Nén các tệp đã quay vòng
    postrotate          # Lệnh thực thi sau khi quay vòng
        /usr/bin/killall -HUP rsyslogd
    endscript           # Kết thúc các lệnh sau khi quay log.
}
```
rotate 7: số lượng bản sao tối đa đc giữ lại
daily; quay vòng hàng ngày
weekly: quay vòng hàng tuần
monthly: quay vòng hàng tháng
yearly: quay vòng hàng năm
missingok: bỏ qua nếu ko tìm thấy file log
notifempty: ko quay vòng nếu tệp file log rỗng
delaycompress: nén các bản sao sau khi quay vòng 
compress: nén các bản sao đã quay vòng
postrotate: lệnh thực thi sau khi quay vòng

endscript: kết thúc các  lệnh sau khi quay vòng

