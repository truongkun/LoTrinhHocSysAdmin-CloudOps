# Giới thiệu về Linux Shell và Shell Scripting

- Khi chúng ta đang sử dụng bất kỳ tiếp với shell. hệ điều hành chính nào, chúng ta đang tương tác gián tiếp
- Trong khi chạy Ubuntu, Linux Mint hoặc bất kỳ bản phân phối Linux nào là chúng ta đang tương tác với shell bằng cách sử dụng thiết bị đầu cuối.

- `Thiết bị đầu cuối` là: các thiết bị kết nối với mạng hoặc hệ thống giao tiếp
    - VD: máy tính cá nhân, điện thoại di động, máy tính bảng, máy chơi game, máy in, camera, thiết bị IoT (Internet of Things), và nhiều thiết bị khác.

# kernel là gì?

- `Kernel` là phần trung tâm của hệ điều hành, làm nhiệm vụ quản lý tài nguyên phần cứng và cung cấp các dịch vụ cần thiết cho các phần mềm ứng dụng.
    - Quản lý tập tin
    - Quản lý quy trình 
    - Quản lý dữ liệu đầu vào/đầu ra 
    - Quản lý bộ nhớ
    - Quản lý thiết bị


> Hệ thống Linux hoàn chỉnh = Kernel + các tiện ích và thư viện hệ thống GNU + các tập lệnh quản lý khác + tập lệnh cài đặt.

## Shell là gì?

- Shell là một chương trình người dùng đặc biệt `cung cấp giao diện cho người dùng sử dụng các dịch vụ của hệ điều hành.` 
- Shell `chấp nhận các lệnh mà con người có thể đọc được từ người dùng và chuyển đổi chúng thành thứ mà kernel có thể hiểu được.`

- Shell được phần thành 2 loại:
    - Command Line Shell 
    - Graphical shell

### Command Line Shell
- Người dụng có thể truy cập shell bằng giao diện dòng lệnh.

- Nó cho phép người dùng lưu trữ các lệnh trong một tệp và thực hiện chúng cùng nhau. 

### Graphical shell?

- Các shell đồ họa cung cấp phương tiện để thao tác các chương trình dựa trên giao diện đồ họa người dùng (GUI), bằng cách cho phép thực hiện các thao tác như mở, đóng, di chuyển và thay đổi kích thước các cửa sổ cũng như chuyển tiêu điểm giữa các cửa sổ. 

**Có một số loại shell có sẵn trên hệ thống linux**

- `BASH:` Đây là shell được sử dụng rộng rãi nhất trong các hệ thống Linux. Nó được sử dụng làm shell đăng nhập mặc định trong hệ thống Linux và macOS.

- `CSH:` Cú pháp của C shell và cách sử dụng nó rất giống với ngôn ngữ lập trình C.

- `KSH:` Korn Shell cũng là cơ sở cho các thông số kỹ thuật tiêu chuẩn POSIX Shell, v.v.

**Shell Scripts**: 
- Nó hoạt động như một trung gian giữa người dùng và nhân Linux, cho phép người dùng kiểm soát và thao tác hệ thống thông qua các lệnh.

- Khi chúng ta viết các lệnh này trong một tệp và có thể thực thi chúng trong shell để tránh công việc lặp đi lặp lại.
- Tập tin shell thường co đuôi ".sh" 
VD: myscript.sh

### Tại sao chúng ta cần shell script?

- Có nhiều lý do để viết shell script:

    - Để tránh công việc lặp đi lặp lại và tự động hóa
      - Quản trị viên hệ thống sử dụng tập lệnh shell để sao lưu định kỳ.
      - Giám sát Hệ Thống
      - Thêm chức năng mới vào shell, v.v.

### Một số ưu điểm của shell script

- Lệnh và cú pháp hoàn toàn giống với những lệnh được nhập trực tiếp vào dòng lệnh, do đó lập trình viên không cần phải chuyển sang cú pháp hoàn toàn khác
- Viết shell script nhanh hơn nhiều
- Bắt đầu nhanh
- Gỡ lỗi tương tác, v.v.

### Một số nhược điểm của shell script

- Dễ xảy ra những sai sót tốn kém, một sai sót nhỏ cũng có thể làm thay đổi lệnh và có thể gây hại.
- Tốc độ thực hiện chậm
- Lỗi thiết kế trong cú pháp hoặc cách triển khai ngôn ngữ
- Không phù hợp với nhiệm vụ lớn và phức tạp
- Cung cấp cấu trúc dữ liệu tối thiểu không giống như các ngôn ngữ kịch bản khác.