# RAID 

`RAID` (Redundant Array of Independent Disks) là một phương pháp tổ chức và quản lý dữ liệu trên nhiều ổ đĩa cứng để tăng cường hiệu suất, độ tin cậy hoặc cả hai.

## Khái niệm và cấu trúc của RAID,

- Khái niệm: `RAID` `kết hợp nhiều ổ đĩa thành một` tập hợp để tạo ra một lưu trữ dữ liệu với các tính năng như `tăng tốc độ, tăng dung lượng hoặc tăng tính sẵn sàng của dữ liệu.`

- Cấu trúc: Mỗi `cấu trúc RAID` bao gồm một số ổ đĩa cứng, được kết hợp với nhau theo một cấu trúc xác định để đạt được mục tiêu cụ thể của RAID. Các cấu trúc phổ biến bao gồm RAID 0, RAID 1, RAID 5, RAID 6, và RAID 10, v.v.

### Nguyên lý hoạt động raid 0,1,5

**RAID 0 (Striping):**

- Nguyên lý hoạt động: `Dữ liệu được chia thành các phần nhỏ (stripes) và lưu trữ trên các ổ đĩa khác nhau.` Cả `hai ổ đĩa hoạt động song song để cải thiện hiệu suất.`
  - Ưu điểm: `Tăng tốc độ đọc/ghi dữ liệu` vì `dữ liệu được chia thành các phần nhỏ và ghi đồng thời` lên nhiều ổ đĩa.
  - Nhược điểm: `Không có tính sẵn sàng` dữ liệu, `mất mát một ổ đĩa sẽ dẫn đến mất toàn bộ dữ liệu trên hệ thống RAID.`

**RAID 1 (Mirroring):**

- Nguyên lý hoạt động: `Dữ liệu được sao chép hoàn toàn lên các ổ đĩa phụ`(mirror drives). Mỗi dữ liệu `đều có một bản sao` trên ổ đĩa khác.
  - Ưu điểm: `Tăng tính sẵn sàng dữ liệu` vì dữ liệu `có thể được truy cập ngay lập tức từ ổ đĩa phụ khi ổ đĩa chính gặp sự cố.`
  - Nhược điểm: `Tăng chi phí vì cần nhiều ổ đĩa` hơn, `hiệu suất ghi có thể giảm do việc phải ghi dữ liệu lên nhiều ổ đĩa cùng một lúc.`

**RAID 5 (Striping with Parity):**

- Nguyên lý hoạt động: `Dữ liệu được chia thành các phần nhỏ và lưu trữ trên các ổ đĩa khác nhau như RAID 0`. Ngoài ra, một phần nhỏ của `dữ liệu được dùng để tính toán và lưu trữ dữ liệu dự phòng (parity data) trên tất cả các ổ đĩa.`
  - Ưu điểm: `Kết hợp tốc độ của RAID 0 với tính sẵn sàng của RAID 1`. Nếu một ổ đĩa `gặp sự cố, dữ liệu có thể được tái tạo từ dữ liệu dự phòng.`
  - Nhược điểm: `Hiệu suất ghi có thể giảm do tính toán dữ liệu dự phòng`. `Tăng tính sẵn sàng dữ liệu nhưng không cao như RAID 1 trong trường hợp nhiều ổ đĩa gặp sự cố cùng một lúc.`Cần `ít nhất 3 ổ cứng.`ứng

## Dưới đây là một so sánh giữa hiệu suất đọc/ghi và độ an toàn dữ liệu của từng loại RAID (RAID 0, RAID 1, RAID 5) so với việc chỉ sử dụng một ổ cứng thông thường:

|Loại RAID|Hiệu năng đọc/ghi|Độ an toàn dữ liệu	|Mô tả          |
|:--------|:----------------|:------------------|:--------------|
|RAID 0	  |Cao|Thấp	|Tăng hiệu suất bằng cách chia dữ liệu thành các phần nhỏ và lưu trữ trên nhiều ổ đĩa. Tuy nhiên, không có tính sẵn sàng dữ liệu, mất một ổ đĩa sẽ dẫn đến mất toàn bộ dữ liệu.
|RAID 1	|Trung bình	|Cao|Tăng tính sẵn sàng dữ liệu bằng cách sao chép dữ liệu hoàn toàn lên một ổ đĩa phụ (mirror drive). Hiệu suất đọc tương đối giống với ổ đĩa thông thường, nhưng hiệu suất ghi có thể giảm do việc phải ghi dữ liệu lên hai ổ đĩa cùng một lúc.
|RAID 5	|Trung bình - Cao	|Cao	|Kết hợp hiệu suất của RAID 0 với tính sẵn sàng dữ liệu của RAID 1. Dữ liệu được chia thành các phần nhỏ và lưu trữ trên nhiều ổ đĩa, và có một phần dữ liệu dự phòng được tính toán và lưu trữ trên các ổ đĩa khác. Tăng tính sẵn sàng dữ liệu, nhưng hiệu suất ghi có thể giảm do phải tính toán dữ liệu dự phòng.
|1 ổ đĩa thông thường	|Trung bình	|Thấp	|`Ổ đĩa đơn lẻ không cung cấp tính năng bảo mật dữ liệu hoặc khả năng phục hồi sau sự cố.`

`Lưu ý:` Đánh giá này chỉ là một tổng quan về hiệu năng và độ an toàn dữ liệu của mỗi loại RAID so với việc sử dụng chỉ một ổ đĩa cứng thông thường. Hiệu suất cụ thể có thể thay đổi tùy thuộc vào cấu hình cụ thể của hệ thống và yêu cầu của ứng dụng