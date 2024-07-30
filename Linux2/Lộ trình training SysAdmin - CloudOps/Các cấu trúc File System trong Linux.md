# Các cấu trúc File System trong Linux:

Trong hệ điều hành Linux, cấu trúc file system thường tuân thủ một số quy ước chung nhằm tổ chức và quản lý các tệp tin và thư mục. Dưới đây là một số thư mục quan trọng trong cấu trúc file system của Linux:

1. **/** (Root Directory):
   - Là `thư mục gốc` của hệ thống file Linux. Tất cả các thư mục và tệp tin khác đều được chứa trong thư mục này.

2. **/bin** (Binaries):
   - Chứa các lệnh cơ bản và các `chương trình thực thi` cần thiết cho việc quản lý và vận hành hệ thống.

3. **/boot**:
   - Chứa các file khởi động của hệ thống, bao gồm các `kernel` và các file cấu hình boot loader như GRUB.

4. **/etc** (Etcetera):
   - Chứa các `tập tin cấu hình` cho các chương trình và dịch vụ trong hệ thống.

5. **/home**:
   - Là nơi lưu trữ các thư mục cá nhân cho các người dùng.

6. **/lib** (Libraries):
   - Chứa các thư viện chia sẻ cần thiết cho các chương trình thực thi trong /bin và /sbin.

7. **/media**:
   - Thường được sử dụng để tự động gắn kết các thiết bị lưu trữ như đĩa CD/DVD hoặc USB.

8. **/mnt** (Mount):
   - Thường được sử dụng để tạm thời gắn kết các thiết bị lưu trữ khác như đĩa mạng hoặc ổ đĩa cắm ngoài.

9. **/opt** (Optional):
   - Chứa các ứng dụng cài đặt bổ sung, thường là các ứng dụng thương mại hoặc phần mềm từ bên thứ ba.

10. **/root**:
    - Thư mục cá nhân của người dùng root (quản trị viên hệ thống).

# Các thư mục và chức năng:

- **/bin**: Chứa các `lệnh thực thi cơ bản, như ls, cp, mv.` 

- **/boot**: Chứa các `file boot loader và kernel` của hệ thống.

- **/etc**: Chứa các `tập tin cấu hình` cho `hệ thống và các ứng dụng.`

- **/home**: Là nơi chứa `thư mục cá nhân`của các người dùng.

- **/lib**: Chứa các `thư viện cần thiết cho các chương trình thực thi trong /bin và /sbin.`

- **/media**: Thường được sử dụng để `gắn kết các thiết bị lưu trữ như USB hoặc đĩa CD/DVD.`

- **/mnt**: Thường được sử dụng để `gắn kết các thiết bị lưu trữ tạm thời.`

- **/opt**: Thường chứa các `ứng dụng cài đặt bổ sung.`

- **/root**: Thư mục `cá nhân của người dùng root.`
  
Mỗi thư mục có một mục đích và chức năng riêng trong cấu trúc file system của Linux, giúp tổ chức và quản lý các tệp tin và thư mục một cách có tổ chức và hiệu quả.