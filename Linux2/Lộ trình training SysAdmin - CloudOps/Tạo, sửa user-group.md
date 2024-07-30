# Các lệnh tạo, sửa user/group

Trong hệ thống Linux, để tạo, sửa đổi người dùng (user) và nhóm (group), chúng ta sử dụng các lệnh như `useradd`, `usermod`, `userdel`, `groupadd`, `groupmod`, và `groupdel`. Dưới đây là mô tả và cách sử dụng của mỗi lệnh:

### 1. Tạo, sửa và xóa người dùng:

- **Tạo người dùng (`useradd`):**
  ```
  sudo useradd [tùy_chọn] username
  ```
  Ví dụ: `sudo useradd john` tạo một người dùng mới có tên là "john".

- **Sửa đổi thông tin người dùng (`usermod`):**
  ```
  sudo usermod [tùy_chọn] username
  ```
  Ví dụ: `sudo usermod -c "John Doe" john` sửa thông tin của người dùng "john".

- **Xóa người dùng (`userdel`):**
  ```
  sudo userdel [tùy_chọn] username
  ```
  Ví dụ: `sudo userdel -r john` xóa người dùng "john" cùng với thư mục home của anh ta (`-r`).

### 2. Tạo, sửa và xóa nhóm:

- **Tạo nhóm (`groupadd`):**
  ```
  sudo groupadd groupname
  ```
  Ví dụ: `sudo groupadd team1` tạo một nhóm mới có tên là "team1".

- **Sửa đổi thông tin nhóm (`groupmod`):**
  ```
  sudo groupmod [tùy_chọn] groupname
  ```
  Ví dụ: `sudo groupmod -g 1001 team1` sửa đổi ID nhóm của nhóm "team1" thành 1001.

- **Xóa nhóm (`groupdel`):**
  ```
  sudo groupdel groupname
  ```
  Ví dụ: `sudo groupdel team1` xóa nhóm "team1" khỏi hệ thống.

**Lưu ý:**
- Trong một số trường hợp, bạn cần phải sử dụng quyền superuser (thông qua `sudo`) để thực hiện các thay đổi về người dùng và nhóm.
- Trước khi thực hiện các thay đổi, hãy đảm bảo rằng bạn hiểu rõ tác động của các thao tác đó và hỏi ý kiến của quản trị hệ thống nếu cần.