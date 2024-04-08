# Using System Log Files: syslogd, rotating log files,

## Log File là gì?

- `Log File` là một tập tin chứa các bản ghi (log entries) về các sự kiện, hoạt động hoặc thông tin cụ thể được ghi lại bởi một hệ thống, ứng dụng hoặc dịch vụ. 

- Mỗi `log entry` trong log file thường bao gồm thông tin như thời gian, nguồn gốc của sự kiện, mức độ ưu tiên (như thông tin, cảnh báo, lỗi), và thông tin chi tiết về sự kiện cụ thể.

## Log file chứa ở đâu?
- Log file chứa ở /var/log

**Trong hệ điều hành Linux, các file log của hệ thống thường được lưu trong các định dạng khác nhau và ở các vị trí khác nhau trên hệ thống. 
Dưới đây là một số file log phổ biến:**

1. **/var/log/messages** hoặc **/var/log/syslog**: Đây là nơi lưu trữ các thông điệp hệ thống chung, bao gồm cả các thông báo từ kernel và các ứng dụng hệ thống.

2. **/var/log/auth.log**: File log này chứa các thông tin liên quan đến xác thực và quản lý người dùng, bao gồm các hoạt động đăng nhập, đăng xuất và thay đổi mật khẩu.

3. **/var/log/secure**: Tương tự như auth.log, file log này cũng chứa các thông tin về xác thực và quản lý người dùng, nhưng thường được sử dụng trên các hệ thống dựa trên CentOS và các bản phân phối tương tự.

4. **/var/log/kern.log**: Chứa các thông báo từ kernel, bao gồm các lỗi và cảnh báo liên quan đến phần cứng và phần mềm của hệ thống.

5. **/var/log/boot.log**: Lưu trữ thông tin liên quan đến quá trình khởi động của hệ thống.

6. **/var/log/daemon.log**: Chứa thông tin từ các dịch vụ daemon chạy trên hệ thống.

7. **/var/log/cron**: File log này chứa các thông tin về các hoạt động được lên lịch bởi cron.

8. **/var/log/apache2/access.log** và **/var/log/apache2/error.log**: Các file log này chứa thông tin về các yêu cầu và lỗi từ máy chủ web Apache.

Đây chỉ là một số file log phổ biến trên hệ thống Linux. Các ứng dụng cụ thể khác cũng có thể tạo ra các file log riêng trong các vị trí khác nhau trên hệ thống.

## Syslog là gì?

- `Syslog` được sử dụng trong hệ thống Linux với mục đích thu thập, lưu trữ và xử lý các thông điệp log từ các ứng dụng, dịch vụ và kernel trên hệ thống.

**Sử dụng syslog:**

- `Thu thập thông tin log:` Syslog thu thập các thông điệp log từ nhiều nguồn khác nhau trên hệ thống, bao gồm cả hệ thống, kernel, dịch vụ và ứng dụng.

- `Ghi thông điệp log vào file log:` Syslog ghi các thông điệp log này vào các file log cục bộ, giúp quản trị viên hệ thống kiểm tra và theo dõi hoạt động của hệ thống, phát hiện và xử lý các lỗi, cảnh báo và vấn đề khác.

- `Chuyển tiếp thông điệp log đến máy chủ syslog từ xa:` Syslog cũng có khả năng chuyển tiếp các thông điệp log đến máy chủ syslog từ xa thông qua giao thức mạng, cho phép tập trung quản lý và giám sát các thông điệp log từ nhiều hệ thống khác nhau.

- `Xác định mức độ ưu tiên (priority) của thông điệp log:` Các thông điệp log được đánh dấu với mức độ ưu tiên khác nhau, từ debug đến emergency, giúp quản trị viên xác định mức độ quan trọng của từng thông điệp và ưu tiên xử lý.

**Tại sao syslog quan trọng:**

- `Giám sát hệ thống:` Syslog cung cấp thông tin quan trọng để giám sát hoạt động của hệ thống, bao gồm các lỗi, cảnh báo và hoạt động của người dùng.

- `Phát hiện và xử lý sự cố:` Syslog giúp phát hiện và xử lý các sự cố và lỗi trên hệ thống, bao gồm cả các vấn đề về bảo mật và hiệu suất.

- `Ghi lại lịch sử hoạt động:` Syslog ghi lại lịch sử hoạt động của hệ thống và ứng dụng, hữu ích cho việc kiểm tra và phân tích sau này.

- `Quản lý log:` Syslog cung cấp cơ chế quản lý log mạnh mẽ, cho phép quản trị viên quản lý, lọc và xử lý các thông điệp log theo nhiều cách khác nhau.

**Bản chất của syslog trong Linux bao gồm các thành phần chính sau:**

- `Syslog Daemon:` Trong môi trường Linux, syslog daemon (hoặc syslogd) là một dịch vụ chạy trên hệ thống, chịu trách nhiệm thu thập các thông điệp log từ các ứng dụng và dịch vụ khác và xử lý chúng theo cách được cấu hình.

- Các Thông Điệp Log (`Log Messages`): Các thông điệp log được sinh ra bởi các ứng dụng, dịch vụ hoặc kernel trên hệ thống. Các thông điệp này có thể chứa thông tin về các sự kiện hệ thống, hoạt động của người dùng, lỗi, cảnh báo và nhiều loại thông tin khác.

- `Cấu Hình Syslog:` Syslog daemon được cấu hình thông qua tệp cấu hình chính (/etc/syslog.conf hoặc /etc/rsyslog.conf trên một số bản phân phối Linux), trong đó quy định các quy tắc cho việc xử lý các thông điệp log. Cấu hình này xác định cách mà các thông điệp log được ghi vào các file log cục bộ hoặc được chuyển tiếp đến máy chủ syslog từ xa.

- `File Log:` Các thông điệp log được ghi vào các file log cục bộ, thường nằm trong thư mục /var/log hoặc các thư mục con của nó. Các file log này thường chứa các thông điệp log của hệ thống, kernel, auth, cron và nhiều dịch vụ khác.

- `Syslog Protocol:` Syslog sử dụng một giao thức mạng đơn giản để gửi các thông điệp log từ các thiết bị và ứng dụng đến máy chủ syslog. Giao thức này là một giao thức không bảo mật và hoạt động trên cổng UDP 514 mặc định.

## Logrotate là gì?

- `Logratate` là một chương trình có sẵn trên hệ điều hành Linux giúp `hỗ trợ quản lý các log files – một yếu tố quan trọng để lập trình viên theo dõi tình trạng hệ thống`
- `Logrotate` giúp xoay vòng file log, nén, di chuyển, gửi tự động,… trong hệ thống.

![alt text](img/logrotate.png)

Trong đó, 
- xoay vòng (rotate) ở đây được hiểu là tiến trình xử lý file log cũ theo quy trình có sẵn (nén/xóa/di chuyển) đồng thời tạo ra file log mới theo thời gian. 
- Logrotate hoạt động tự động mà không cần can thiệp bằng thao tác thủ công nhờ các thiết lập thông qua file cấu hình.

**Tính năng của Logrotate**

- Logrotate cung cấp các tính năng cơ bản trong quản lý file log như sau:
  - Xoay vòng file log cho đến khi đáp ứng dung lượng đã được thiết lập.
  - Ghi tiếp dữ liệu log vào file mới khi đã hoàn thành xoay vòng.
  - Nén file log đã xoay vòng.
  - Tùy chọn kiểu nén file log.
  - Thêm ngày tháng vào tên file khi thực hiện xoay vòng.
  - Thực thi shell script khi xoay vòng file log.
  - Xóa các file xoay vòng cũ.

**Các cấu hình Logrotate trên Linux**

- Toàn bộ thông tin `log files` mà `Logrotate` quản lý được lưu tại `/etc/logrotate.conf`, tại đây chứa các thông tin như chu kỳ lặp, nén file, dung lượng file log,… Còn thông tin về cấu hình file log đối với từng ứng dụng được lưu tại `/etc/logrotate.d/`.

- Nhìn chung, cấu trúc của cấu hình `Logrotate` khá đơn giản, chỉ gồm các `log file` và các thông tin thiết lập cấu hình được đặt trong dấu `{ }`. Ngay sau đây chúng tôi sẽ giới thiệu cụ thể hơn về một số cấu hình phổ biến nhất:

**Cách thực hiện Rotate Log thường bao gồm:**

- `Xác định tiêu chí quay vòng:` Điều này có thể bao gồm kích thước tệp, thời gian hoặc số lượng bản ghi trong nhật ký.

- `Đặt lịch trình quay vòng:` Xác định thời điểm hoặc điều kiện mà quá trình quay vòng sẽ được kích hoạt. Ví dụ, có thể là mỗi ngày, mỗi tuần hoặc khi kích thước tệp nhật ký vượt quá một ngưỡng nhất định.

- `Sao lưu và di chuyển nhật ký cũ:` Khi điều kiện quay vòng được kích hoạt, các tệp nhật ký cũ sẽ được sao lưu và di chuyển đến một vị trí khác hoặc được đổi tên để làm sạch không gian lưu trữ.

- `Tạo nhật ký mới:` Sau khi nhật ký cũ đã được di chuyển hoặc đổi tên, một tệp nhật ký mới sẽ được tạo ra để tiếp tục ghi lại các sự kiện mới.

**Việc thực hiện Rotate Log là cần thiết vì nó mang lại một số lợi ích quan trọng:**

- `Quản lý không gian lưu trữ:` Ngăn chặn các tệp nhật ký phình to và chiếm quá nhiều không gian lưu trữ trên hệ thống.

- `Tiện ích trong việc theo dõi và phân tích:` Nhật ký được quay vòng có thể dễ dàng quản lý và theo dõi hơn, giúp việc phân tích và xác định sự cố hoặc vấn đề trở nên dễ dàng hơn.

- `Hiệu suất hệ thống:` Giảm thiểu tác động của việc ghi nhật ký lớn lên hiệu suất hệ thống.

Tóm lại, `Rotate Log` là một phần quan trọng của quản lý hệ thống, giúp duy trì sự ổn định và hiệu suất của nó thông qua việc quản lý nhật ký một cách hiệu quả.






