# Mount

Lệnh "mount" trong hệ thống Linux được sử dụng để gắn một hệ thống tệp hoặc thiết bị vào cây thư mục của hệ thống tệp, cho phép truy cập vào dữ liệu được lưu trữ trên đó. Dưới đây là một số cách sử dụng thông thường của lệnh "mount":

1. **Xem Danh Sách Các Thiết Bị và Phân Vùng Đã Gắn**: Bạn có thể sử dụng lệnh "mount" mà không có bất kỳ đối số nào để hiển thị danh sách các thiết bị và phân vùng đã được gắn trên hệ thống của bạn.

    ```
    mount
    ```

2. **Gắn Một Thiết Bị hoặc Phân Vùng**: Để gắn một thiết bị hoặc phân vùng vào hệ thống tệp, bạn cần chỉ định thiết bị và điểm gắn (thư mục) muốn sử dụng.

    ```
    sudo mount /dev/sdb1 /mnt
    ```

    Trong ví dụ này, `/dev/sdb1` là thiết bị hoặc phân vùng mà bạn muốn gắn, và `/mnt` là thư mục mục tiêu bạn muốn gắn vào.

3. **Gắn Các Hệ Thống Tệp Mạng (NFS, Samba, vv)**: Bạn có thể sử dụng lệnh "mount" để gắn các hệ thống tệp mạng như NFS hoặc Samba bằng cách chỉ định địa chỉ IP của máy chủ và thư mục chia sẻ.

    ```
    sudo mount -t nfs 192.168.1.100:/shared /mnt/nfs
    ```

4. **Gắn Tệp ISO hoặc Tệp Hệ Thống Tệp Khác**: Nếu bạn có một tệp ISO hoặc một hệ thống tệp khác, bạn có thể sử dụng lệnh "mount" để gắn chúng vào một thư mục trống.

    ```
    sudo mount -o loop file.iso /mnt/iso
    ```

    Trong đó, `file.iso` là tệp ISO mà bạn muốn gắn, và `/mnt/iso` là điểm gắn mục tiêu.

5. **Gắn Thiết Bị Tạm Thời (tmpfs)**: Bạn cũng có thể tạo một hệ thống tệp tạm thời trong bộ nhớ (tmpfs) bằng cách sử dụng lệnh "mount".

    ```
    sudo mount -t tmpfs none /mnt/tmpfs
    ```

Để biết thêm thông tin chi tiết về các tùy chọn và cách sử dụng của lệnh "mount", bạn có thể kiểm tra trợ giúp bằng cách sử dụng "man mount".