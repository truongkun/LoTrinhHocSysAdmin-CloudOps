# StartUp Script là gì?

- `Startup script` là một tập lệnh, tập tin hoặc tập hợp các hành động được thực hiện tự động khi hệ thống được khởi động. 
- Các `startup script` thường được thực thi cùng với boot loader khi máy tính hoặc máy chủ được khởi động.

- Công dụng chính của startup script là thiết lập môi trường làm việc hoặc chạy các dịch vụ và ứng dụng cần thiết khi hệ thống bắt đầu hoạt động. 
- Các startup script có thể chứa các câu lệnh để:
  
  - Khởi động các dịch vụ hệ thống như Apache, MySQL, hoặc các daemon khác.
  - Thiết lập biến môi trường.
  - Tạo ra các thiết lập hệ thống như gắn kết các phân vùng, thiết lập cấu hình mạng, và nhiều hơn nữa.
  - Chạy các ứng dụng hoặc tác vụ cần thiết để khởi động hệ thống.

Startup script có thể được thiết lập để chạy tại các giai đoạn cụ thể trong quá trình khởi động của hệ thống, như:

- Trước khi root filesystem được mount.
- Sau khi root filesystem được mount nhưng trước khi các dịch vụ chính thức được khởi động.
- Sau khi tất cả các dịch vụ chính đã được khởi động.

Cách cụ thể để tạo và cấu hình startup script có thể khác nhau tùy thuộc vào hệ điều hành và bản phân phối cụ thể mà bạn đang sử dụng. Trong một số hệ điều hành như Linux, bạn có thể sử dụng các thư mục như `/etc/init.d/` hoặc `/etc/rc.d/` để lưu trữ các script khởi động, trong khi trên các hệ điều hành khác như systemd, bạn sẽ sử dụng các unit files để định nghĩa các dịch vụ.

# Chạy 1 script mỗi khi server đc bật lên 

- Trong hệ điều hành Ubuntu, bạn có thể sử dụng systemd để cấu hình và quản lý các dịch vụ và startup script. Đây là cách để tạo và cấu hình một systemd service để chạy một script mỗi khi server được bật lên:

1. Tạo một script bạn muốn chạy khi hệ thống khởi động. Ví dụ, hãy tạo một tệp script có tên `myscript.sh` trong thư mục `/usr/local/bin/`:

```bash
sudo nano /usr/local/bin/myscript.sh
```

Trong tệp `myscript.sh`, thêm các câu lệnh mà bạn muốn chạy khi hệ thống được khởi động. Ví dụ:

```bash
#!/bin/bash
# Script example
echo "Hello, world!" > /var/log/myscript.log
```

Lưu và đóng tệp.

2. Cấp quyền thực thi cho script:

```bash
sudo chmod +x /usr/local/bin/myscript.sh
```

3. Tạo một systemd service unit để chạy script này:

```bash
sudo nano /etc/systemd/system/myscript.service
```

Trong tệp `myscript.service`, thêm các cấu hình cho service unit:

```plaintext
[Unit]
Description=My Script Service
After=network.target

[Service]
Type=simple
ExecStart=/usr/local/bin/myscript.sh

[Install]
WantedBy=multi-user.target
```

Lưu và đóng tệp.

4. Bây giờ, bạn cần reload systemd để cập nhật danh sách các dịch vụ:

```bash
sudo systemctl daemon-reload
```

5. Kích hoạt service để nó chạy mỗi khi hệ thống được khởi động:

```bash
sudo systemctl enable myscript.service
```

6. Bây giờ, bạn có thể kiểm tra trạng thái của service và khởi động nó:

```bash
sudo systemctl start myscript.service
sudo systemctl status myscript.service
```

Service này sẽ được chạy mỗi khi hệ thống được khởi động và ghi "Hello, world!" vào tệp `/var/log/myscript.log`.