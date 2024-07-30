# Tìm hiểu về StartUp Script

- `StartUp Script` là một thuật ngữ thường được sử dụng trong lĩnh vực công nghệ thông tin để `chỉ một đoạn mã hoặc tập lệnh được thực thi tự động` khi một hệ thống hoặc máy tính được khởi động. Đây thường là một cách để cấu hình hoặc chuẩn bị môi trường làm việc trước khi hệ thống hoạt động.

- Cách sử dụng `Startup Script` thường thực hiện thông qua việc tạo và chỉnh sửa một tập tin `script`, sau đó thiết lập để được thực thi khi hệ thống khởi động. Dưới đây là một ví dụ về cách sử dụng `Startup Script` trên các hệ điều hành khác nhau:

**Trên Linux:**

1. Mở trình soạn thảo văn bản như Vim hoặc Nano.

2. Viết mã script của bạn. 

    Ví dụ: 
        
        #!/bin/bash
        echo "Hello, this is a startup script!"

3. Lưu tập tin với định dạng .sh.

4. Cấp quyền thực thi cho tập tin: 

        chmod +x script.sh.

5. Đặt tập tin này trong thư mục `/etc/init.d/ hoặc /etc/rc.local.`