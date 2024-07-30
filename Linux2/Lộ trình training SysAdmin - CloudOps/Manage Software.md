#  Manage Software

## I. "package" trong Linux có nghĩa gì?

- `package` (gói phần mềm) là một tập hợp các file và thông tin liên quan được đóng gói cùng nhau để cài đặt và quản lý phần mềm. Mỗi gói phần mềm thường bao gồm các file thực thi, thư viện, tài liệu, và các thông tin cần thiết khác như phiên bản, tác giả, và phụ thuộc vào các gói khác.

**Có nhiều định dạng gói phổ biến trong các hệ thống Linux như:**

1. RPM (Red Hat Package Manager): Sử dụng trong các bản phân phối như Red Hat Enterprise Linux (RHEL), CentOS, Fedora và các bản phân phối dựa trên RPM.

2. DEB: Được sử dụng trong các bản phân phối dựa trên Debian như Debian và Ubuntu.

3. APT (Advanced Package Tool): Là công cụ quản lý gói cho hệ thống Debian và các phân phối dựa trên Debian như Ubuntu.

Gói phần mềm giúp việc cài đặt, cập nhật và gỡ bỏ phần mềm trở nên dễ dàng và có thể tự động hóa, giúp người dùng quản lý hệ thống một cách hiệu quả hơn.

## II. Dependencies là gì?

`dependencies` (phụ thuộc) là các thành phần, thư viện, hoặc gói phần mềm mà một ứng dụng hoặc dự án cần để hoạt động đúng cách.


> Bản chất của gói phụ thuộc (dependency) là mối quan hệ giữa các thành phần trong một hệ thống phần mềm, trong đó một thành phần cần sử dụng các chức năng hoặc tài nguyên của thành phần khác để hoạt động đúng đắn.

**Các dependencies có thể bao gồm:**

1. `Thư viện và module`: Các phần mềm thường cần sử dụng các thư viện hoặc module để thực hiện các chức năng cụ thể. 

    - `Ví dụ`, một ứng dụng web có thể phụ thuộc vào các thư viện như Flask hoặc Django trong Python để xây dựng các ứng dụng web.

2. `Gói phần mềm`: Các ứng dụng cũng có thể phụ thuộc vào các gói phần mềm khác để thực hiện các chức năng cụ thể. 
   - Ví dụ, một ứng dụng có thể cần một gói phần mềm như MySQL để truy cập cơ sở dữ liệu.

3. `Phiên bản`: Dependencies thường có yêu cầu về phiên bản cụ thể. Một ứng dụng có thể yêu cầu một phiên bản cụ thể của một thư viện hoặc gói phần mềm để đảm bảo tính tương thích và ổn định.

4. `Hệ điều hành`: Đôi khi, dependencies cũng có thể liên quan đến hệ điều hành mà phần mềm cần chạy trên. Một ứng dụng có thể chỉ chạy trên một hệ điều hành cụ thể hoặc yêu cầu một số tính năng đặc biệt của hệ điều hành.

Quản lý `dependencies` là một phần quan trọng của quá trình phát triển phần mềm và triển khai ứng dụng, vì việc `thiếu sót dependencies` hoặc không quản lý chúng một cách hiệu quả có thể dẫn đến các lỗi hoặc vấn đề về tính tương thích.

Đối với người dùng, quản trị viên hệ thống, hoặc các công cụ quản lý gói, quản lý dependencies thường được tự động hoặc thông qua các lệnh quản lý gói.

**cách sử dụng dependencies khi cài đặt và quản lý gói phần mềm:**

1. `Cài đặt gói phần mềm và dependencies`: Khi bạn cài đặt một gói phần mềm, hệ thống sẽ tự động kiểm tra và cài đặt các `dependencies` cần thiết. 

   - Ví dụ, nếu bạn muốn cài đặt gói `nginx`, nhưng gói này cần sử dụng các thư viện như `openssl`, hệ thống sẽ cài đặt cả `nginx` và `openssl` cho bạn.

2. `Quản lý dependencies`: Các công cụ quản lý gói như `apt`, `yum`, `dnf` sẽ tự động quản lý các `dependencies`. Khi bạn cài đặt, cập nhật hoặc gỡ bỏ một gói phần mềm, các công cụ này sẽ kiểm tra và quản lý `dependencies` để đảm bảo rằng hệ thống của bạn hoạt động một cách ổn định.

3. `Kiểm tra dependencies`: Bạn có thể kiểm tra các `dependencies` của một gói phần mềm bằng cách sử dụng các lệnh tương ứng với công cụ quản lý gói. 

   - Ví dụ, để kiểm tra `dependencies` của gói `nginx` trên Ubuntu hoặc Debian, bạn có thể sử dụng lệnh:

            apt-cache show nginx

    Lệnh này sẽ `hiển thị thông tin chi tiết` về gói `nginx`, bao gồm cả các `dependencies` của nó

`Quản lý dependencies` là một phần quan trọng của việc quản lý phần mềm trên hệ điều hành Linux, giúp đảm bảo tính ổn định và hoạt động đúng đắn của hệ thống.

## III. Binary package là gì?

### 3.1. Định nghĩa về binary package.

- `Binary package (gói nhị phân)` là một dạng đóng gói của phần mềm đã được biên dịch thành mã máy `(binary code)` thay vì mã nguồn `(source code)`. Điều này có nghĩa là phần mềm đã được chuyển đổi thành dạng mà máy tính có thể `hiểu và thực thi trực tiếp mà không cần phải biên dịch thêm`.

- `Binary packages` thường được sử dụng để `cài đặt phần mềm` một cách dễ dàng và nhanh chóng trên hệ thống Linux. Thay vì tải mã nguồn và biên dịch phần mềm từ đầu, người dùng có thể sử dụng `binary packages` để cài đặt trực tiếp từ kho lưu trữ `(repository)` của hệ thống.

> Bản chất của gói nhị phân (binary package) là một tập hợp các tệp tin chứa mã máy (binary code) đã được biên dịch từ mã nguồn của một phần mềm. Gói nhị phân thường bao gồm các tệp tin thực thi, thư viện, tài nguyên và các tệp tin cấu hình cần thiết cho phần mềm hoạt động.

### 3.2. Cách sử dụng binary packages

### 3.2.1.Sử dụng apt trên Ubuntu/Debian:

- Để cài đặt một binary package, bạn có thể sử dụng lệnh apt install:

        sudo apt install <package_name>

- Ví dụ: sudo apt install firefox để cài đặt trình duyệt Firefox.

### 3.2.2. Sử dụng yum/dnf trên CentOS/RHEL/Fedora:

- Sử dụng yum (trước CentOS/RHEL 8) hoặc dnf (từ CentOS/RHEL 8 trở đi) để cài đặt binary packages:

        sudo yum install <package_name>

    hoặc

        sudo dnf install <package_name>

- Ví dụ: sudo dnf install nginx để cài đặt máy chủ web Nginx.

### 3.2.3. Sử dụng zypper trên openSUSE:

- Sử dụng lệnh zypper install để cài đặt binary packages:

        sudo zypper install <package_name>

- Ví dụ: sudo zypper install chromium để cài đặt trình duyệt Chromium.

Khi sử dụng các công cụ quản lý gói như `apt, yum, dnf, zypper`, hệ thống sẽ tự động `tải` và `cài đặt binary packages` cùng với các `dependencies` cần thiết cho phần mềm mà bạn muốn cài đặt. Điều này giúp bạn tiết kiệm thời gian và năng lượng so với việc tự biên dịch từ mã nguồn.

## IV. Repository (kho lưu trữ) là gì?

### 4.1. Định nghĩa

- `Repository (kho lưu trữ)` là nơi chứa các `binary packages (gói nhị phân)` và các thông tin liên quan khác về phần mềm. Các `repository` cung cấp một cách tiện lợi để tìm kiếm, cài đặt và cập nhật phần mềm trên hệ thống Linux.

- Các `repository` thường được quản lý và duy trì bởi cộng đồng hoặc các tổ chức phát triển phần mềm. 
  - Các bản phân phối Linux như `Ubuntu, Debian, CentOS, Fedora, và openSUSE` đều có các `repository` mặc định được cài đặt sẵn, và người dùng có thể thêm các `repository` khác nếu cần.

- Để kiểm tra các `repository` đang được cấu hình trên hệ thống Linux của bạn, bạn có thể sử dụng các lệnh tương ứng với công cụ quản lý gói mà bạn đang sử dụng. 

**Dưới đây là một số ví dụ:**
1. Sử dụng apt trên Ubuntu/Debian:

        cat /etc/apt/sources.list

2. Sử dụng yum trên CentOS/RHEL:

        yum repolist

3. Sử dụng dnf trên Fedora

        dnf repolist

4. Sử dụng zypper trên openSUSE:

        zypper repos

>Khi bạn chạy các lệnh này, hệ thống sẽ hiển thị danh sách các `repository` đã được cấu hình trên máy tính của bạn, bao gồm cả tên, URL và trạng thái của từng `repository`. Điều này giúp bạn biết được các nguồn phần mềm mà hệ thống của bạn có thể truy cập để tìm kiếm và cài đặt các gói phần mềm.

## V. Các cách cài phần mềm

**Có 2 cách cài phần mềm phổ biến**

- là sử dụng gói nhị phân từ repository hoặc biên dịch từ mã nguồn. Dưới đây là hướng dẫn thực hành cả hai cách này:

### 1. Cài đặt phần mềm từ gói nhị phân (binary package) từ repository:

Bước 1: Cập nhật danh sách gói phần mềm

- Trước tiên, hãy đảm bảo rằng danh sách gói phần mềm trên hệ thống của bạn đã được cập nhật:

  - Trên Ubuntu/Debian:

        sudo apt update

  - Trên CentOS/RHEL:

        sudo yum update

Bước 2: Cài đặt phần mềm

- Sau khi cập nhật danh sách gói phần mềm, bạn có thể sử dụng lệnh cài đặt để cài đặt phần mềm. 

  - Ví dụ: để cài đặt trình duyệt web Firefox trên `Ubuntu/Debian`, bạn có thể sử dụng lệnh sau:

        sudo apt install firefox

  - Trên CentOS/RHEL:

        sudo yum install firefox

### 2. Biên dịch từ mã nguồn:

Bước 1: Tải mã nguồn

- Trước tiên, bạn cần tải mã nguồn của phần mềm từ trang web chính thức hoặc từ kho mã nguồn như GitHub.

Bước 2: Giải nén và di chuyển vào thư mục mã nguồn
- Sau khi tải xuống, giải nén tệp tin và di chuyển vào thư mục mã nguồn của phần mềm:

        tar -zxvf <tên_file.tar.gz>
        cd <thư_mục_mã_nguồn>

Bước 3: Biên dịch và cài đặt

- Tiếp theo, bạn cần biên dịch và cài đặt phần mềm từ mã nguồn. Thông thường, bạn sẽ cần chạy các lệnh sau:
 
        ./configure
        make
        sudo make install

    Lưu ý rằng quá trình này có thể mất thời gian và có thể cần một số thư viện phụ thuộc.

**Lưu ý:**
- Sử dụng cách cài đặt từ gói nhị phân từ repository là phương pháp đơn giản và nhanh chóng hơn.
- Biên dịch từ mã nguồn thường được sử dụng khi không có gói nhị phân sẵn hoặc khi bạn muốn tùy chỉnh các tùy chọn biên dịch.