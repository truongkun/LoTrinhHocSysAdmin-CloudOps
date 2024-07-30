# LogRotate
### Rotate Log là gì?

`Rotate Log` là quá trình quản lý và duy trì các tệp log trong hệ thống một cách hiệu quả bằng cách chia nhỏ các tệp log thành các phần nhỏ hơn hoặc xoá các tệp cũ để giữ cho dung lượng của tệp log không quá lớn. Quá trình này giúp hạn chế sự tiêu tốn dung lượng đĩa và giúp quản trị viên hệ thống dễ dàng quản lý và phân tích các thông tin log.

### Tại sao phải thực hiện việc Rotate Log?

1. **Quản lý dung lượng đĩa**: Các tệp log có thể nhanh chóng trở nên lớn và chiếm nhiều dung lượng trên đĩa. Việc xoá các tệp log cũ hoặc chia nhỏ chúng giúp hạn chế sự tiêu tốn dung lượng đĩa.

2. **Dễ dàng quản lý**: Các tệp log quá lớn có thể làm cho việc phân tích và tìm kiếm thông tin trong chúng trở nên khó khăn. Rotate Log giúp phân chia log thành các phần nhỏ hơn, dễ dàng quản lý và tra cứu.

3. **Bảo mật thông tin**: Rotate Log cũng giúp bảo mật thông tin bằng cách giảm thiểu rủi ro lộ thông tin nhạy cảm trong các tệp log cũ.

### Cấu hình Rotate Log cho `/var/log/syslog`:

Để cấu hình Rotate Log cho `/var/log/syslog`, chúng ta sử dụng công cụ `logrotate`. Dưới đây là một ví dụ về cấu hình Rotate Log cho `/var/log/syslog`:

1. Tạo một tệp cấu hình mới cho `/var/log/syslog` trong thư mục `/etc/logrotate.d/`.

   ```
   sudo nano /etc/logrotate.d/syslog
   ```

2. Thêm cấu hình sau vào tệp cấu hình:

   ```
   /var/log/syslog {
       rotate 7
       daily
       missingok
       notifempty
       delaycompress
       compress
       postrotate
           /usr/bin/killall -HUP rsyslogd
       endscript
   }
   ```

   - `rotate 7`: Giữ lại tối đa 7 bản sao của tệp log.
   - `daily`: Rotate log mỗi ngày.
   - `missingok`: Bỏ qua nếu tệp log không tồn tại.
   - `notifempty`: Không xoá tệp log nếu nó trống.
   - `delaycompress`: Hoãn việc nén tệp log sau khi xoá.
   - `compress`: Nén các tệp log cũ.
   - `postrotate ... endscript`: Sau khi xoá tệp log, thực hiện lệnh để restart dịch vụ syslog.

3. Lưu và đóng tệp cấu hình.

4. Đảm bảo rằng dịch vụ `logrotate` đang chạy tự động trong cron jobs. Thông thường, nó sẽ được cài đặt sẵn và chạy tự động, nhưng nếu không, bạn có thể thêm vào cron jobs.

   ```
   sudo nano /etc/cron.daily/logrotate
   ```

5. Khởi động lại dịch vụ `rsyslog` để áp dụng các thay đổi.

   ```
   sudo systemctl restart rsyslog
   ```

Quá trình cấu hình này sẽ Rotate Log cho `/var/log/syslog` hàng ngày, giữ lại tối đa 7 bản sao của tệp log và nén các tệp log cũ sau khi xoá.