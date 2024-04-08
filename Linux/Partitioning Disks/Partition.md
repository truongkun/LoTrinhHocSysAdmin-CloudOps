# Partition(phân vùng) là gì?

- `Partition` đề cập đến việc chia một ổ đĩa thành các phần vùng riêng biệt, mỗi phần vùng này có thể được sử dụng để lưu trữ dữ liệu, hệ thống tệp, hoặc các mục đích khác. Mỗi partition có thể được xử lý như một ổ đĩa riêng lẻ, với các thuộc tính và quyền riêng biệt.

**Dưới đây là một số khái niệm cơ bản về partition trong Linux:**

1. **Primary Partition**: Đây là các phân vùng cơ bản trên ổ đĩa, có thể chứa hệ thống tệp hoặc dữ liệu.

2. **Extended Partition**: Trong một số trường hợp, bạn có thể cần chia ổ đĩa thành nhiều hơn số lượng primary partition tối đa cho phép. Extended partition cho phép bạn tạo ra các logical partition bổ sung bên trong nó.

3. **Logical Partition**: Các phân vùng này được tạo bên trong extended partition và không giới hạn bởi số lượng primary partition tối đa. Chúng được sử dụng khi bạn cần nhiều hơn số lượng primary partition cho hệ thống của mình.

4. **File System**: Mỗi partition có thể được định dạng với một loại hệ thống tệp cụ thể như ext4, XFS, NTFS, v.v. Hệ thống tệp quyết định cách dữ liệu được tổ chức và lưu trữ trên partition.

5. **Mount Point**: Đây là vị trí trong hệ thống tệp của Linux mà partition được gắn kết để truy cập dữ liệu trong đó.

6. **Swap Partition**: Ngoài các partition lưu trữ dữ liệu, Linux còn sử dụng partition swap để quản lý bộ nhớ ảo.

Quản lý partition trên Linux thường được thực hiện thông qua các công cụ như `fdisk`, `parted`, hoặc `GParted`.

## - Phân biệt được file system với partition và mối liên hệ giữa chúng trong server 

Dưới đây là một bảng phân biệt giữa file system và partition cũng như mối liên hệ giữa chúng trong server:

Dưới đây là bảng đã sửa đổi cho phù hợp:

| Đặc điểm        | Partition                                       | File System                                      |
|-----------------|-------------------------------------------------|--------------------------------------------------|
| Định nghĩa      | Phần của ổ đĩa được chia ra thành các phân vùng | Cách dữ liệu được tổ chức và lưu trữ trên partition |
| Mục đích        | Phân vùng ổ đĩa để phân biệt và quản lý dữ liệu | Xác định cách dữ liệu được tổ chức và lưu trữ      |
| Định dạng       | Có thể được tạo ra với MBR hoặc GPT            | Được định dạng với các loại như ext4, NTFS, v.v. |
| Quản lý         | Có thể tạo, xóa, thay đổi kích thước và định dạng partition | Có thể tạo, định dạng, mount và unmount file system |
| Mối liên hệ     | Một ổ đĩa có thể chứa nhiều partition          | Mỗi partition chứa một file system duy nhất      |
| Ví dụ           | /dev/sda1, /dev/sdb2                             | ext4, NTFS, FAT32, XFS, v.v.                      |

</br>

**Dưới đây là một số điểm khác biệt giữa MBR và GPT:**

**1.MBR (Master Boot Record):**

- Hỗ trợ tối đa 4 phân vùng chính (primary partitions).
- Nếu cần nhiều hơn 4 phân vùng, bạn có thể sử dụng phân vùng mở rộng (extended partition) để chứa các phân vùng logic (logical partitions).
- Hạn chế kích thước ổ đĩa tối đa là 2 TB.


**2.GPT (GUID Partition Table):**

- Hỗ trợ tối đa 128 phân vùng, không có sự phân biệt giữa phân vùng chính và phân vùng logic.
- Hỗ trợ kích thước ổ đĩa lớn hơn, không có hạn chế như MBR.
- Cung cấp bảo mật cao hơn với việc có các bản sao lưu dữ liệu của bảng phân vùng và mã kiểm tra sai sót.                |

**Dưới đây là một số hệ thống tệp phổ biến và thường được sử dụng trên các hệ thống Linux:**

- ext4: Là một trong những hệ thống tệp phổ biến nhất trên hệ thống Linux. Nó cung cấp nhiều tính năng như hỗ trợ dung lượng lớn, journaling, và hỗ trợ tập tin lớn.

- NTFS (New Technology File System): Là hệ thống tệp tiêu chuẩn trên hệ điều hành Windows từ Windows NT 3.1 trở lên. NTFS hỗ trợ tính năng bảo mật, nén dữ liệu, và phục hồi lỗi tốt.

- XFS: Là một hệ thống tệp phổ biến trên các hệ thống Linux, đặc biệt là cho các ứng dụng yêu cầu hiệu suất cao và xử lý tệp lớn.

Mối liên hệ giữa partition và file system là rằng mỗi partition thường chứa một loại file system duy nhất. Khi một partition được tạo ra, bạn có thể định dạng nó với một loại file system cụ thể (ví dụ: ext4, NTFS, v.v.), và sau đó mount nó vào hệ thống tệp của bạn để có thể truy cập và sử dụng dữ liệu trên đó.