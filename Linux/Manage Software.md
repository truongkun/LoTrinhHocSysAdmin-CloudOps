# Manage Software

## Package

- là 1 một tập hợp các tệp tin và thông tin liên quan được đóng gói lại thành một đơn vị cài đặt. 

## Dependencies

- là gói phần mềm mà gói khác cần để hoạt động đứng đắn

## Binary package

- là 1 gói phần mềm trong đó tất  cả các tệp tin đã được biên dịch sẵn thành mã nhị phân

## Repository 

- Repository (kho lưu trữ) là một kho chứa các gói phần mềm hoặc mã nguồn, thường được quản lý bởi hệ thống quản lý gói (package manager) trên hệ thống Linux. 
- Bản chất của repository là cung cấp một nguồn tài nguyên đáng tin cậy để cài đặt, cập nhật và quản lý phần mềm trên hệ thống.

**Kiểm tra các repo của máy đang dùng.**

> cat /etc/apt/sources.list


## Có 3 cách phổ biến:

1. Cài đặt từ kho lưu trữ (repository) bằng trình quản lý gói mặc định của hệ thống (ví dụ: APT trên Ubuntu, YUM/DNF trên CentOS/Fedora).

2. Tải xuống và cài đặt từ mã nguồn.

4. Sử dụng gói nhị phân (binary package) đã được tải xuống.

### Cách 1: Cài đặt từ kho lưu trữ (repository) bằng trình quản lý gói mặc định:

> sudo apt-get update
    sudp apt-get insrtall vim

### Cách 2: Cài đặt từ mã nguồn

**Ví dụ: Cài đặt trình soạn thảo văn bản Vim từ mã nguồn trên Ubuntu:**
  
```
# Cài đặt các phụ thuộc cần thiết
sudo apt update
sudo apt install -y build-essential ncurses-dev

# Tải xuống mã nguồn của Vim
wget https://github.com/vim/vim/archive/master.tar.gz
tar -xzvf master.tar.gz
cd vim-master

# Biên dịch và cài đặt Vim
./configure
make
sudo make install
```

### Cách 3: Sử dụng goí nhị phân đã được tải xuống.

```
# Tải xuống gói nhị phân của Google Chrome
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb

# Cài đặt gói nhị phân
sudo apt install ./google-chrome-stable_current_amd64.deb

```

## Liệt kê tất cả các gói đã được cài đặt trên hệ thống:

> sudo apt list --installed

>dpkg -l

**Kiểm tra xem một gói cụ thể đã được cài đặt hay chưa (ví dụ: Vim):**

> dpkg -l | grep vim