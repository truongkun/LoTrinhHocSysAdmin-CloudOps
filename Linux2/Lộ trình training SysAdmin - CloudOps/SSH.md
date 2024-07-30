# SSH

`SSH (Secure Shell)` là một giao thức mạng dùng để `thiết lập kết nối an toàn và mã hóa giữa hai thiết bị, cho phép người dùng truy cập và điều khiển máy chủ từ xa qua mạng Internet.` SSH cung cấp một cách để mã hóa dữ liệu gửi qua mạng để đảm bảo rằng thông tin nhạy cảm không bị lộ ra ngoài và ngăn chặn các cuộc tấn công của người thứ ba.

Dưới đây là một số khái niệm cơ bản và nguyên tắc của SSH:

1. **Mã hóa**: SSH sử dụng mã hóa để bảo vệ dữ liệu truyền qua mạng. Các thông điệp được mã hóa trước khi chúng được gửi đi và giải mã sau khi chúng được nhận. Điều này giúp ngăn chặn bất kỳ ai nghe trộm hoặc chiếm đoạt dữ liệu trên đường truyền.

2. **Xác thực**: SSH cung cấp các phương pháp xác thực để đảm bảo rằng người dùng được phép truy cập vào máy chủ. Các phương pháp này bao gồm xác thực bằng mật khẩu, xác thực bằng cặp khóa công khai và khóa riêng, và xác thực bằng các phương pháp khác như token RSA hoặc biometrics.

3. **Cặp khóa công khai và riêng**: SSH sử dụng một cặp khóa gồm khóa công khai và khóa riêng. Khóa riêng được lưu trữ trên máy tính cá nhân của người dùng, trong khi khóa công khai được lưu trữ trên máy chủ mà người dùng muốn truy cập. Khi kết nối, máy chủ sẽ yêu cầu người dùng chứng minh họ sở hữu khóa riêng bằng cách sử dụng khóa công khai. 

4. **Cổng mặc định**: Cổng mặc định của SSH là 22. Tuy nhiên, nó có thể được cấu hình để sử dụng các cổng khác để tăng tính bảo mật.

5. **Sử dụng trong hệ thống Unix/Linux**: SSH thường được sử dụng phổ biến trong các hệ thống Unix và Linux để truy cập và quản lý từ xa.

6. **Sử dụng trong mạng LAN và Internet**: SSH không chỉ được sử dụng để truy cập từ xa vào máy chủ trên Internet mà còn trong các mạng LAN nội bộ để tránh việc truyền dữ liệu không mã hóa qua mạng nội bộ.

Như vậy, SSH đóng vai trò quan trọng trong việc bảo vệ thông tin và tăng tính bảo mật cho việc truy cập từ xa vào hệ thống.

## Lệnh ssh -add 

Lệnh `ssh-add` được sử dụng để thêm các khóa SSH vào môi trường SSH-Agent, một công cụ được sử dụng để quản lý các khóa SSH trên hệ thống. Khi bạn thực hiện kết nối SSH, SSH-Agent sẽ tự động sử dụng các khóa được thêm vào nó để xác thực mà không cần phải yêu cầu bạn nhập mật khẩu.

**Dưới đây là cú pháp cơ bản của lệnh `ssh-add`:**

```
ssh-add [tùy chọn] [khóa SSH]
```

**Các tùy chọn phổ biến:**

- `-l`: Liệt kê các khóa SSH đã được thêm vào SSH-Agent.
- `-d`: Xóa một khóa SSH khỏi SSH-Agent.
- `-D`: Xóa tất cả các khóa SSH khỏi SSH-Agent.
- `-t`: Xác định thời gian sống (timeout) cho khóa SSH được thêm vào SSH-Agent.

**Ví dụ sử dụng:**

1. Thêm một khóa SSH vào SSH-Agent:

    ```
    ssh-add ~/.ssh/id_rsa
    ```

- Trong đó `~/.ssh/id_rsa` là đường dẫn đến khóa riêng. Sau khi thực hiện lệnh này, bạn có thể thực hiện kết nối SSH mà không cần phải nhập mật khẩu.

2. Liệt kê các khóa SSH đã được thêm vào SSH-Agent:

    ```
    ssh-add -l
    ```

3. Xóa một khóa SSH khỏi SSH-Agent:

    ```
    ssh-add -d ~/.ssh/id_rsa
    ```

- Trong đó `~/.ssh/id_rsa` là đường dẫn đến khóa riêng cần xóa.

>Lệnh `ssh-add` rất hữu ích khi bạn cần sử dụng nhiều khóa SSH và muốn tự động quản lý chúng để thực hiện kết nối mà không cần nhập mật khẩu mỗi lần.

## Tạo và sử dụng ssh-key để ssh được vào 1 server. phân biệt public key và private key. 

Để SSH vào một máy chủ, bạn cần tạo cặp khóa SSH, bao gồm khóa riêng (private key) và khóa công khai (public key). Dưới đây là hướng dẫn cụ thể về cách tạo và sử dụng cặp khóa SSH:

### 1. Tạo cặp khóa SSH:

Bạn có thể tạo cặp khóa SSH bằng cách sử dụng lệnh `ssh-keygen`. Hãy mở terminal và thực hiện các bước sau:

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

Trong đó:
- `-t rsa`: Chọn thuật toán mã hóa RSA.
- `-b 4096`: Độ dài của khóa (ở đây là 4096 bit, tăng cường tính bảo mật).
- `-C "your_email@example.com"`: Thêm một nhận xét để dễ dàng nhận biết khóa.

Khi được hỏi về vị trí để lưu trữ khóa, bạn có thể chọn vị trí mặc định hoặc chỉ định một vị trí tùy chỉnh.

### 2. Sao chép khóa công khai lên máy chủ:

Sau khi tạo khóa, bạn cần sao chép nội dung của khóa công khai (`~/.ssh/id_rsa.pub` mặc định) lên máy chủ mà bạn muốn SSH vào.

```bash
ssh-copy-id username@hostname
```

Thay `username` bằng tên người dùng trên máy chủ và `hostname` bằng địa chỉ hoặc tên máy chủ.

### 3. Sử dụng khóa SSH để kết nối:

Bây giờ bạn đã có thể sử dụng khóa SSH để kết nối vào máy chủ mà không cần mật khẩu:

```bash
ssh username@hostname
```

### Phân biệt khóa riêng (Private Key) và khóa công khai (Public Key):

- **Khóa Riêng (Private Key)**:
  - Là phần bí mật của cặp khóa SSH.
  - Được lưu trữ trên máy tính cá nhân của bạn.
  - Được sử dụng để xác thực với máy chủ khi bạn kết nối SSH.
  - Không bao giờ được chia sẻ hoặc tiết lộ cho bất kỳ ai khác.

- **Khóa Công Khai (Public Key)**:
  - Là phần công khai của cặp khóa SSH.
  - Được sao chép và lưu trữ trên máy chủ mà bạn muốn truy cập.
  - Được sử dụng để xác thực bạn khi bạn kết nối từ máy tính cá nhân đến máy chủ.
  - Có thể được chia sẻ với bất kỳ ai hoặc bất kỳ máy chủ nào mà bạn muốn truy cập. Không gây nguy cơ nếu bị tiết lộ.

## Tạo ssh key có passphrase. Khi muốn cho phép 1 user cần ssh vào server bằng key thì cần làm gì

Để tạo một SSH key với passphrase và sau đó cho phép một người dùng SSH vào máy chủ bằng khóa này, bạn có thể thực hiện các bước sau:

### 1. Tạo SSH key với passphrase:

1. Mở terminal trên máy tính của bạn.

2. Sử dụng lệnh `ssh-keygen` để tạo một cặp khóa SSH. Khi được hỏi, bạn cần nhập passphrase.

    ```bash
    ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
    ```

    Bạn sẽ được hỏi về vị trí để lưu trữ khóa. Mặc định là `~/.ssh/id_rsa` và `~/.ssh/id_rsa.pub`.

### 2. Sao chép khóa công khai lên máy chủ:

1. Sử dụng lệnh `ssh-copy-id` để sao chép khóa công khai lên máy chủ:

    ```bash
    ssh-copy-id username@hostname
    ```

    Thay `username` bằng tên người dùng trên máy chủ và `hostname` bằng địa chỉ hoặc tên máy chủ.

2. Điền passphrase của bạn khi được yêu cầu.

### 3. Cấu hình máy chủ để sử dụng khóa này:

1. Mở tệp cấu hình SSH trên máy chủ. Điều này thường là `/etc/ssh/sshd_config`.

2. Đảm bảo rằng `PubkeyAuthentication` được thiết lập thành `yes`. Nếu nó không, bạn có thể thay đổi nó bằng cách chỉnh sửa tệp cấu hình và sau đó khởi động lại dịch vụ SSH:

    ```
    PubkeyAuthentication yes
    ```

3. Lưu lại tệp cấu hình và khởi động lại dịch vụ SSH:

    ```bash
    sudo service ssh restart
    ```

### 4. Kiểm tra kết nối:

1. Bây giờ, bạn hoặc người dùng đã được thêm vào khóa SSH có thể kết nối vào máy chủ bằng cách sử dụng passphrase cho khóa riêng.

    ```bash
    ssh username@hostname
    ```

    Hoặc nếu passphrase đã được thêm vào SSH-Agent:

    ```bash
    ssh-add ~/.ssh/id_rsa
    ssh username@hostname
    ```

Khi kết nối, hệ thống sẽ yêu cầu bạn nhập passphrase của khóa riêng. Sau khi bạn nhập đúng, bạn sẽ được kết nối vào máy chủ mà không cần nhập mật khẩu.
