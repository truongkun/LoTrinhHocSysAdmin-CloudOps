# Monitoring Disk: ‘df’, ‘du’

- Để kiểm tra dung lượng đĩa trống và sử dụng, bạn có thể sử dụng hai lệnh là "df" và "du". 

## Lệnh "df":

1. **df -h**: Hiển thị thông tin về dung lượng, sử dụng và dung lượng trống của các hệ thống tệp được kết nối, với các giá trị được hiển thị ở dạng dễ đọc (ví dụ: KB, MB, GB).

![alt text](/img/df.png)

- Trong đó:
  - filesystem: tên filesystem có thể trùng với phân vùng đĩa.
  - 1K-blocks: Số lượng khối (block) có trong filesystem có kích thước 1Kb.
  - Used: Số lượng 1K-block được sử dụng trong filesystem.
  - Available: Số lượng 1K-block đang có sẵn.
  - Use%: Phần trăm đĩa đã sử dụng trong filesystem.
  - Mounted on: Nơi mount.

**Lệnh df -h:**

- Lệnh `df` được đi kèm với một số tùy chọn để hiển thị nội dung rõ ràng và thân thiện với người dùng hơn.
- Tùy chọn -h cho ta một cái nhìn trực quan hơn khi đọc các thông số ở chế độ chi tiết : bytes, megabytes và gigabytes.

![alt text](/img/df%20-h.png)

## Lệnh "du":

- Lệnh `du` là một công cụ dòng lệnh được cung cấp bởi Linux, nhằm báo cáo dung lượng ổ đĩa được sử dụng bởi các thư mục và file. Lệnh `du` là viết tắt của từ “disk usage”. Đây là công cụ chính để phân tích không gian ổ đĩa trong dòng lệnh.

Lệnh "du" trong hệ thống Linux được sử dụng để hiển thị thông tin về dung lượng sử dụng của các tập tin và thư mục trong hệ thống tệp. Dưới đây là một số tùy chọn phổ biến của lệnh "du":

1. **-h, --human-readable**: Hiển thị kích thước theo định dạng dễ đọc, như "K" cho kilobytes, "M" cho megabytes, vv.
2. **-s, --summarize**: Hiển thị chỉ tổng dung lượng của các thư mục được chỉ định, không phải là mỗi tệp trong đó.
3. **-c, --total**: Hiển thị tổng dung lượng của tất cả các thư mục hoặc tệp được chỉ định, cộng lại với nhau.
4. **-a, --all**: Hiển thị kích thước của tất cả các tập tin, thay vì chỉ thư mục.
5. **--exclude=pattern**: Loại bỏ các tập tin hoặc thư mục khớp với mẫu chỉ định.
6. **-d, --max-depth=N**: Giới hạn số cấp thư mục được hiển thị trong kết quả.
7. **-L, --dereference**: Hiển thị kích thước của tệp mà một liên kết mềm trỏ đến thay vì liên kết mềm chính nó.
8. **--time**: Hiển thị thời gian tạo, sửa đổi và truy cập của tệp.

Ví dụ:
- `du -h`: Hiển thị dung lượng theo định dạng dễ đọc.
- `du -sh /path/to/directory`: Hiển thị chỉ tổng dung lượng của thư mục được chỉ định.
- `du -ach /path/to/directory`: Hiển thị tổng dung lượng của tất cả các tập tin và thư mục, cộng lại với nhau, và sử dụng định dạng dễ đọc.
- `du -h --max-depth=1 /path/to/directory`: Hiển thị chỉ dung lượng của các thư mục cấp 1 trong thư mục được chỉ định, với định dạng dễ đọc.

Đây chỉ là một số tùy chọn cơ bản của lệnh "du". Để biết thêm thông tin và tùy chọn khác, bạn có thể tham khảo tài liệu hướng dẫn hoặc sử dụng "man du" để xem trợ giúp chi tiết.

## Sự khác biệt giữa "df" và "du":


Dưới đây là một bảng so sánh giữa lệnh "du" và "df" trong hệ thống Linux:

| Đặc Điểm            | du (Disk Usage)                           | df (Disk Free)                              |
|----------------------|--------------------------------------------|---------------------------------------------|
| Mô Tả                | Hiển thị dung lượng được sử dụng bởi các tập tin và thư mục trong hệ thống tệp. | Hiển thị thông tin về dung lượng đĩa và không gian trống. |
| Phạm Vi              | Áp dụng cho từng tệp và thư mục riêng lẻ. | Áp dụng cho toàn bộ phân vùng hoặc hệ thống tệp. |
| Đơn Vị Đo            | Thường hiển thị kích thước dưới dạng byte hoặc các đơn vị lớn hơn như KB, MB, GB. | Thường hiển thị kích thước dưới dạng KB, MB, GB hoặc TB. |
| Hiển Thị Dung Lượng  | Hiển thị thực tế dung lượng được sử dụng bởi tệp tin và thư mục, có thể bao gồm các tệp ẩn và các tệp được ẩn. | Hiển thị tổng dung lượng và dung lượng trống của phân vùng hoặc hệ thống tệp. |
| Ẩn/Ngoại Trừ Tệp    | Có thể loại bỏ các tệp cụ thể hoặc thư mục bằng cách sử dụng tùy chọn --exclude. | Không cung cấp khả năng ẩn hoặc loại bỏ các tệp cụ thể. |
| Tương Tác            | Thường được sử dụng để kiểm tra dung lượng của một số tệp cụ thể hoặc thư mục. | Thường được sử dụng để kiểm tra tổng dung lượng và không gian trống của toàn bộ phân vùng hoặc hệ thống tệp. |

Điều quan trọng cần lưu ý là "du" và "df" là hai công cụ khác nhau được thiết kế để cung cấp thông tin về dung lượng lưu trữ từ các góc độ khác nhau. "du" tập trung vào hiển thị dung lượng được sử dụng của các tệp và thư mục cụ thể, trong khi "df" thường được sử dụng để kiểm tra tổng dung lượng và không gian trống của toàn bộ phân vùng hoặc hệ thống tệp.

1. **df** (Disk Free) là lệnh được sử dụng để kiểm tra dung lượng trống và sử dụng của các hệ thống tệp được kết nối. Nó không phân tích chi tiết về từng tệp hay thư mục mà chỉ cung cấp tổng quan về dung lượng đĩa.

2. **du** (Disk Usage) là lệnh được sử dụng để kiểm tra dung lượng của các thư mục và tệp cụ thể. Nó cung cấp thông tin chi tiết về dung lượng của từng thư mục và tệp trong hệ thống tệp.