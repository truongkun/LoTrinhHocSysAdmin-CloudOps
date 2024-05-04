# Chi tiết cách sửa lỗi Checksum bằng lệnh fsck trong Linux

**Các tùy chọn của lệnh fsck**
- fsck -A: Kiểm tra tất cả các hệ thống file.
- fsck -C: Hiển thị thanh tiến trình có đang hoạt động hay không.
- fsck -l: Khóa thiết bị để đảm bảo không có chương trình nào khác cố gắng sử dụng phân vùng trong quá trình kiểm tra.
- fsck -M: Hệ thống file được mount sẽ không kiểm tra.
- fsck -P: Kiểm tra hệ thống file là song song hay không bao gồm root.
- fsck -R: Lệnh sẽ không kiểm tra hệ thống file root.
- fsck -r: Lệnh cung cấp thông tin thiết bị đã được kiểm tra hay chưa.
- fsck -T: Lệnh không hiển thị tiêu đề.
- fsck -V: Cung cấp mô tả những gì đang được thực hiện.

## Khi nào bạn nên sử dụng lệnh fsck trong Linux

- Có những tình huống khác nhau khi bạn muốn chạy fsck. 

- Dưới đây là một số ví dụ:

  - Hệ thống không khởi động được.
  - Các tệp trên hệ thống bị hỏng (thường thấy lỗi đầu vào/đầu ra).
  - Ổ đĩa kết nối (bao gồm ổ flash/thẻ SD) không hoạt động như mong đợi.


## Làm thế nào để sử dụng lệnh fsck?

Bước 1: Đầu tiên, hãy mở tùy chọn boot và chọn Advanced options for Ubuntu.

![alt text](/Linux/img/fsck1.png)

Bước 2: Sau đó chọn chế độ Recovery.

![alt text](/Linux/img/fsck2.png)

Bước 3: Sau đó chọn tùy chọn fsck.

![alt text](/Linux/img/fsck3.png)

Nó sẽ yêu cầu hệ thống file mount lại. Chọn Yes.

![alt text](/Linux/img/fsck4.png)

Bây giờ, bạn có thể thấy màn hình sau:

![alt text](/Linux/img/fsck5.png)

Bước 4: Chọn Resume.

![alt text](/Linux/img/fsck6.png)

