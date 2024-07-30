# Tìm hiểu về FSCK

## fsck là gì?

`fsck` là một công cụ kiểm tra và sửa chữa các hệ thống tập tin trên các hệ thống Unix-like như Linux. `fsck` viết tắt của "file system check" (kiểm tra hệ thống tập tin). Nó được sử dụng để kiểm tra tính toàn vẹn của hệ thống tập tin và sửa chữa các lỗi mà nó có thể phát hiện.

## Dưới đây là một số điểm chính về `fsck`:

1. **Kiểm tra hệ thống tập tin khi khởi động**: Trong một số trường hợp, hệ thống Linux có thể tự động chạy `fsck` khi khởi động để kiểm tra và sửa chữa các hệ thống tập tin tự động. Điều này thường xảy ra nếu hệ thống không được tắt đúng cách hoặc gặp sự cố đột ngột.

2. **Sử dụng thủ công**: Bạn cũng có thể chạy `fsck` thủ công trên một hệ thống tập tin cụ thể bằng cách sử dụng lệnh trong chế độ sửa đổi (single-user mode) hoặc từ một phân vùng live CD/USB. Lệnh cơ bản để chạy `fsck` là:

   ```
   fsck <device>
   ```

   Trong đó `<device>` là đường dẫn tới phân vùng hoặc thiết bị chứa hệ thống tập tin bạn muốn kiểm tra.

3. **Sửa chữa các lỗi**: `fsck` có khả năng phát hiện và sửa chữa một số loại lỗi phổ biến trên hệ thống tập tin như inode hỏng, block hỏng, hoặc danh sách liên kết hỏng. Tùy thuộc vào mức độ nghiêm trọng của lỗi, `fsck` có thể yêu cầu sự can thiệp của người dùng hoặc thậm chí có thể gây mất dữ liệu.

4. **Cẩn thận khi sử dụng**: Việc sử dụng `fsck` cần phải thận trọng, đặc biệt là trên các hệ thống hoạt động. Một số lỗi có thể dẫn đến mất dữ liệu hoặc làm hỏng hệ thống tập tin. Trước khi chạy `fsck`, bạn nên sao lưu dữ liệu quan trọng trước để đảm bảo an toàn.

## Cách sử dụng fsck

- Để sử dụng `fsck` để kiểm tra và sửa chữa hệ thống tập tin trên Linux, bạn cần chạy lệnh `fsck` với quyền root và chỉ định thiết bị hoặc phân vùng mà bạn muốn kiểm tra. 
- Dưới đây là một ví dụ cụ thể:

  - Giả sử bạn muốn kiểm tra và sửa chữa hệ thống tập tin trên phân vùng `/dev/sda1`. Đầu tiên, bạn cần đảm bảo rằng phân vùng đó không được sử dụng bằng cách đóng tất cả các tiến trình hoặc chuyển sang chế độ single-user mode nếu cần thiết.

    Sau đó, bạn sẽ chạy `fsck` với quyền root như sau:

    ```
    sudo fsck /dev/sda1
    ```

Lưu ý rằng bạn cần thay thế `/dev/sda1` bằng thiết bị hoặc phân vùng cụ thể mà bạn muốn kiểm tra.

Khi bạn chạy lệnh này, `fsck` sẽ kiểm tra hệ thống tập tin trên `/dev/sda1` và hiển thị thông báo về các lỗi có thể được phát hiện. Nếu có lỗi, `fsck` sẽ hỏi bạn liệu bạn muốn sửa chữa chúng hay không. Bạn có thể trả lời "yes" hoặc "y" để cho `fsck` sửa chữa lỗi.

Lưu ý rằng việc chạy `fsck` có thể mất một khoảng thời gian khá lớn, đặc biệt là trên các phân vùng lớn hoặc khi có nhiều lỗi cần sửa chữa. Đồng thời, cẩn thận với việc sửa chữa hệ thống tập tin, vì có thể gây mất dữ liệu nếu không thực hiện đúng cách. Luôn nên sao lưu dữ liệu quan trọng trước khi chạy `fsck`.