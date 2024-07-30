# Configuration File Logging

- Tập tin cấu hình của hệ thống Linux để thiết lập và quản lý các thông tin nhật ký (log). 
>
- Trong hệ thống Linux, các tập tin cấu hình cho việc logging thường được quản lý thông qua một số công cụ và tùy thuộc vào phần mềm cụ thể bạn đang sử dụng. 
>
- Dưới đây là một số tập tin cấu hình chung mà bạn có thể gặp khi làm việc với logging trên Linux:

1. **/etc/rsyslog.conf**: `Rsyslog` là một hệ thống logging phổ biến trên Linux. Tập tin cấu hình này chứa các thiết lập cho rsyslog, bao gồm cách xử lý các bản ghi log từ các nguồn khác nhau và nơi lưu trữ chúng.

2. **/etc/syslog-ng/syslog-ng.conf**: `Syslog-ng` là một hệ thống logging khác và tập tin cấu hình này chứa các thiết lập tương tự như rsyslog.conf, nhưng cho syslog-ng.

3. **/etc/logrotate.conf**: `Logrotate` là một tiện ích được sử dụng để quản lý các tập tin log, bao gồm xoay log để giữ cho chúng không trở nên quá lớn. Tập tin cấu hình này cho phép bạn thiết lập các quy tắc xoay log cho các tập tin cụ thể.

4. **/etc/rsyslog.d/**: Thư mục này chứa các tập tin cấu hình bổ sung cho rsyslog. Bạn có thể tìm thấy các tập tin cấu hình cho các ứng dụng cụ thể tại đây, cho phép bạn định cấu hình cách các ứng dụng ghi log của mình được xử lý.

5. **/etc/logstash/**: `Logstash` là một phần của bộ giải pháp ELK (Elasticsearch, Logstash, Kibana) được sử dụng để thu thập, xử lý và trực quan hóa log. Các tập tin cấu hình cho Logstash thường nằm trong thư mục này.

6. **/etc/nginx/nginx.conf**: Đối với máy chủ web Nginx, tập tin cấu hình chính cũng có thể chứa các thiết lập logging cho Nginx.

Đối với mỗi hệ thống hoặc ứng dụng cụ thể, cách cấu hình logging có thể khác nhau. Việc xem tài liệu hướng dẫn cụ thể cho phần mềm hoặc hệ thống bạn đang sử dụng là một phần quan trọng để hiểu cách cấu hình logging một cách đúng đắn.