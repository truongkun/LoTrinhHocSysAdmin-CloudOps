# Tìm hiểu chowm

Cả hai lệnh `chown` và `chgrp` được sử dụng để thay đổi quyền sở hữu của tệp tin hoặc thư mục trong hệ thống Linux. Dưới đây là mô tả và ví dụ minh họa cho mỗi lệnh:

## 1. `chown`:

- Lệnh `chown` được sử dụng để `thay đổi người sở hữu của một tệp tin hoặc thư mục.`

    **Cú pháp:**
    ```
    chown new_owner[:new_group] file(s)
    ```

    **Ví dụ:**
    Giả sử bạn muốn thay đổi người sở hữu của tệp tin `example.txt` thành `user1`:
    ```
    chown user1 example.txt
    ```
    Nếu bạn muốn thay đổi cả người sở hữu và nhóm của `example.txt` thành `user1` và `group1`:
    ```
    chown user1:group1 example.txt
    ```

## 2. `chgrp`:

- Lệnh `chgrp` được sử dụng để `thay đổi nhóm sở hữu của một tệp tin hoặc thư mục.`

    **Cú pháp:**
    ```
    chgrp new_group file(s)
    ```

    **Ví dụ:**
    Giả sử bạn muốn thay đổi nhóm sở hữu của tệp tin `example.txt` thành `group1`:
    ```
    chgrp group1 example.txt
    ```

## Ví dụ minh họa:

- Giả sử bạn có một tệp tin có tên là `file1.txt` trong thư mục hiện tại. Bây giờ, bạn muốn thay đổi người sở hữu của `file1.txt` thành `user2` và nhóm sở hữu thành `group2`. Bạn có thể sử dụng các lệnh `chown` và `chgrp` như sau:

    ```
    chown user2:group2 file1.txt
    ```

    Sau khi thực thi lệnh này, người sở hữu và nhóm sở hữu của `file1.txt` sẽ được thay đổi thành `user2` và `group2` tương ứng.

    