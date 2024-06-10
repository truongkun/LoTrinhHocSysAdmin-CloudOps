# Ip là gì?

- IP là từ viết tắt của Internet Protocol, được dịch là giao thức của Internet.

## IP tĩnh là gì?

- IP này là địa chỉ được cấu hình thủ công cho các thiết bị kết nối mạng. Nó được gọi là `IP tĩnh` do tính chất cố định và không thể thay đổi. Các thiết bị phải được cấu hình đúng với router để chúng có thể giao tiếp. Điều này cũng là nhược điểm của IP tĩnh. Vì vậy, một số người dùng đã thực hiện chuyển IP từ tĩnh sang động.

## IP tĩnh dùng để làm gì?

- `IP tĩnh` là địa chỉ cố định dành riêng cho một hoặc một nhóm người dùng Internet. Thông thường IP tĩnh sẽ được cấp cho một máy chủ sử dụng với một mục đích riêng biệt, ví dụ máy chủ mail, máy chủ web…, nhằm giúp người dùng không bị gián đoạn trong quá trình truy cập

### Cấu hình ip tĩnh

Để cấu hình địa chỉ IP tĩnh cho một giao diện mạng trên Ubuntu, bạn có thể sử dụng công cụ cấu hình mạng mặc định của Ubuntu hoặc chỉnh sửa các tệp cấu hình thủ công. Dưới đây là cách thực hiện bằng cách sử dụng các công cụ mặc định của Ubuntu:

### Sử dụng công cụ mạng của Ubuntu

1. Mở Terminal trên Ubuntu.

2. Sử dụng lệnh sau để mở tệp cấu hình mạng:
   ```
   sudo nano /etc/netplan/00-installer-config.yaml
   ```

3. Trong tệp này, bạn sẽ thấy một phần về giao diện mạng. Sửa đổi phần này để cấu hình IP tĩnh. Ví dụ:
   ```yaml
   network:
     version: 2
     ethernets:
       eth0:
         addresses:
           - 192.168.1.100/24
         gateway4: 192.168.1.1
         nameservers:
           addresses: [8.8.8.8, 8.8.4.4]
   ```

   - Thay `eth0` bằng tên giao diện mạng của bạn (có thể là `eth0`, `ens33`, `enp0s3`, hoặc một cái khác).
   - `192.168.1.100/24` là địa chỉ IP tĩnh bạn muốn cấu hình.
   - `192.168.1.1` là địa chỉ của cổng gateway.
   - `8.8.8.8` và `8.8.4.4` là các máy chủ DNS (có thể thay đổi tùy thuộc vào mạng của bạn).

4. Lưu và đóng tệp.

5. Sử dụng lệnh sau để áp dụng cấu hình mới:
   ```
   sudo netplan apply
   ```

6. Kiểm tra kết nối bằng cách ping một địa chỉ IP bên ngoài để đảm bảo rằng mọi thứ hoạt động đúng.

### Lưu ý:
- Trong một số trường hợp, tên của giao diện có thể khác nhau. Bạn có thể sử dụng lệnh `ip a` để liệt kê tất cả các giao diện mạng trên hệ thống của mình để xác định tên chính xác của giao diện mạng.
- Đảm bảo bạn có quyền sudo khi thực hiện các lệnh này.

## IP động là gì?

- Địa chỉ IP động là địa chỉ IP được tự động gán cho mỗi kết nối hoặc nút trên mạng, chẳng hạn như trên điện thoại di động, máy tính, máy tính bảng,... .

- Máy chủ DHCP đảm nhận việc gán địa chỉ IP tự động.

- Được biết đến là địa chỉ IP động, bởi vì nó sẽ thay đổi tùy thuộc vào mỗi kết nối mạng khác nhau trong tương lai. Nếu bạn kiểm tra địa chỉ IP trên máy tính và thấy nó tự động thay đổi sau một khoảng thời gian, đó chính là IP động. Ngược lại, nếu địa chỉ IP không thay đổi, đó là IP tĩnh.

- Việc thay đổi địa chỉ IP giúp bạn mở khóa truy cập vào các trang web bị chặn một cách thuận lợi hơn. Đổi địa chỉ IP cũng là biện pháp để ẩn thông tin địa chỉ mạng của bạn nơi bạn làm việc và học tập, tránh sự theo dõi từ bên ngoài.

### Cấu hình ip động.

Để cấu hình IP động cho một giao diện mạng trên Ubuntu 20.04, bạn có thể sử dụng công cụ mạng mặc định của Ubuntu là Netplan. Dưới đây là cách để làm điều này:

1. Mở tệp cấu hình Netplan cho giao diện mạng bạn muốn cấu hình. Tệp này thường được lưu trữ trong thư mục `/etc/netplan/` và có phần mở rộng là `.yaml`. Ví dụ, nếu bạn muốn cấu hình cho giao diện có tên là `ens33`, bạn có thể mở tệp `01-netcfg.yaml` hoặc một tệp tương tự.

2. Sử dụng trình soạn thảo văn bản như `nano` hoặc `vim` để mở tệp cấu hình. Ví dụ:

```
sudo nano /etc/netplan/01-netcfg.yaml
```

3. Trong tệp cấu hình, bạn sẽ thấy một cấu trúc YAML mô tả cấu hình mạng. Đối với IP động, bạn sẽ thấy dòng `dhcp4: true`. Nếu không có, bạn có thể thêm nó vào dưới phần `ethernets` của giao diện mạng bạn muốn cấu hình. Ví dụ:

```
network:
  version: 2
  renderer: networkd
  ethernets:
    ens33:
      dhcp4: true
```

4. Lưu và đóng tệp cấu hình.

5. Sau đó, bạn cần áp dụng cấu hình bằng cách chạy lệnh:

```
sudo netplan apply
```

Sau khi thực hiện các bước này, giao diện mạng sẽ cấu hình để nhận IP động từ máy chủ DHCP trong mạng của bạn. Bạn cũng có thể sử dụng lệnh `ip addr show` để kiểm tra xem IP đã được cấu hình thành công cho giao diện mạng hay chưa.


# khi nào dùng ip động khi nào dùng ip tĩnh

- IP Tĩnh: Dành cho các thiết bị cần truy cập từ nhiều nguồn khác nhau, cung cấp dịch vụ hoặc cần địa chỉ IP cố định để hoạt động ổn định 

- Ip Động: Dành cho các thiết bị người dùng cuối, thiết bị di động, hoặc các thiết bị không cần truy cập từ xa hoặc không cần địa chỉ IP cố định (máy tính cá nhân, điện thoại thông minh, máy tính bảng).

-> Đặt Ip tĩnh khi nó được dùng truy cập từ nhiều nguồn khác đến, còn lại ip động


**Cấu hình IP tĩnh (Static IP):**

- **Khi nào sử dụng:** 
  - Các thiết bị cần địa chỉ IP cố định để dễ dàng quản lý, như máy chủ (server), máy in mạng, camera IP, hoặc các thiết bị yêu cầu truy cập từ xa thường xuyên.
  - Các hệ thống mạng yêu cầu cấu hình địa chỉ IP cụ thể để hoạt động chính xác hoặc để tuân thủ các yêu cầu về bảo mật và quản lý mạng.
  
- **Ưu điểm:**
  - Địa chỉ IP không thay đổi, dễ dàng quản lý và theo dõi thiết bị trong mạng.
  - Tăng tính bảo mật và ổn định cho các dịch vụ yêu cầu địa chỉ IP cố định.
  
- **Nhược điểm:**
  - Quản lý thủ công phức tạp, nhất là trong các mạng lớn.
  - Khả năng xung đột IP nếu không quản lý tốt.

**Cấu hình IP động (Dynamic IP):**

- **Khi nào sử dụng:** 
  - Mạng có nhiều thiết bị di động, như điện thoại, laptop, hoặc các thiết bị không yêu cầu địa chỉ IP cố định.
  - Các hệ thống mạng có số lượng thiết bị lớn và yêu cầu tự động cấp phát địa chỉ IP để giảm thiểu công việc quản lý.
  
- **Ưu điểm:**
  - Tự động cấp phát và quản lý địa chỉ IP qua DHCP, giảm thiểu công việc thủ công.
  - Dễ dàng mở rộng mạng mà không cần cấu hình lại từng thiết bị.
  
- **Nhược điểm:**
  - Địa chỉ IP thay đổi mỗi lần thiết bị kết nối lại, khó quản lý và theo dõi thiết bị cố định.
  - Có thể gặp vấn đề với các dịch vụ yêu cầu địa chỉ IP cố định.