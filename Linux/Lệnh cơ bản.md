# Lệnh cơ bản

`cd:` di chuyển qua lại giữa các thư mục.

`pwd:` xem đường dẫn đang đứng ở đâu

`man:` xem thông tin chi tiết, cách sử  dụng và các option của lệnh đó
    vd: man = tên_lệnh

`cat:` Xem thông tin của file

`tac:` Xem thông tin file từ dưới lên

`sort:` sắp xếp file
- -r: sắp xếp giảm dần
- -k số cột : sắp xếp cột đó lên đầu
- -u: loại bỏ các dòng trung lặp

`split:` chia nhỏ file
  - -b --bytes=SIZE: Chia nhỏ tập tin thành các phần có kích thước cố định là SIZE bytes.
  - -l số dòng, --lines=NUMBER: Chia nhỏ tập tin thành các phần có số dòng là NUMBER.
  - -d --numeric-suffixes: Sử dụng các số thứ tự thay vì các chữ cái làm hậu tố cho các tập 

`uniq:` xóa nhưng từ trùng lặp
- -c: đếm số  dòng
- -i: bỏ qua các dòng trùng lặp liên tiếp, bỏ qua sựu khác biệt về kiểu chữ cái 

`head:` Đọc 10 Dòng đầu
- -n, --line=N: Hiển thị n số dòng

`tail:` Đoc 10 dòng cuối
- -n, --line=N : hiển thị n dòng cuối

`nl:` đánh số thứ tự các dòng trong file

`less:` để xem và duyệt nội dung của một tập tin văn bản một cách tương tác.
- hỗ trợ giao diện: lăn lên/xuống, tìm kiếm, vv.

`cut:` sử dụng để cắt và hiển thị các phần của mỗi dòng từ một tập tin văn bản.
  - -f, --fields=LIST: Chỉ định danh sách các trường để cắt. 
    ```
    Ví dụ, -f 1,3 sẽ cắt ra các trường 1 và 3 từ mỗi dòng.
    ```
  - -d, --delimiter=DELIMITER: Chỉ định ký tự phân cách giữa các trường. Mặc định là TAB.

`wc:` để đếm số lượng dòng, từ và byte trong một tập tin văn bản.
  - -l, --lines: Đếm số lượng dòng.
  - -w, --words: Đếm số lượng từ.
  - -c, --bytes: Đếm số lượng byte.

`grep:` được sử dụng để tìm kiếm các dòng trong một tập tin văn bản hoặc đầu vào từ đầu vào tiêu chuẩn mà khớp với một biểu thức chính quy.
  - -i, --ignore-case: Bỏ qua sự phân biệt chữ hoa chữ thường.
  - -r, --recursive: Tìm kiếm đệ quy trong các thư mục con.
  - -n, --line-number: Hiển thị số dòng cùng với kết quả tìm kiếm.

`sed:` để thực hiện các thao tác chỉnh sửa trên văn bản từ đầu vào tiêu chuẩn hoặc từ tập tin.
  - -e SCRIPT, --expression=SCRIPT: Chỉ định tập lệnh để thực thi.
  - -i, --in-place: Chỉnh sửa tập tin đầu vào trực tiếp.
  - -r, --regexp-extended: Sử dụng biểu thức chính quy mở rộng.

`awk:` để phân tích và xử lý các dòng từ đầu vào văn bản, theo một cách mạnh mẽ và linh hoạt.
  - -F, --field-separator: Định nghĩa ký tự phân cách giữa các trường.
  - -v VAR=VAL: Đặt một biến nội bộ trong awk.
  - '{print $1}': In ra trường đầu tiên của mỗi dòng.

`vim:` chỉnh sửa nội dung file.
- Trong `vim` có 3 chế độ chính:
    - `Command mode(chế độ lệnh):` chế độ mặc định khi mở vim. Chế độ này để thực hiện các hành động như: 
        - phím `h, j, k, l:` để di chuyển.
        - phím `d:` xóa.
        - phím `y:` sao chép.
        - phím `p:` để dán.

    - `Insert mode(chế độ chèn):` Chế độ này để nhập văn bản vào tài liệu, giống như trình soạn thảo văn bản thông thường
        - phím i: để chuyển sang chế độ chèn
        - phím Esc: thoát khỏi chế độ chèn

    - `Ex mode(chế độ Ex):` là chế độ bạn có thể nhập các lệnh Ex (hoặc Ex commands). `Ex` là một ngôn ngữ lệnh mạnh mẽ trong Vim được sử dụng để thực hiện các tác vụ phức tạp hoặc lặp lại. Bạn có thể vào chế độ Ex bằng cách nhập `:` ở chế độ lệnh.
        - một số lệnh Ex phổ biến:
            - `:w:` Lưu tập tin (tương tự như :save).
            - `:q:` Thoát khỏi Vim (tương tự như :quit).
            - `:q!:` Thoát khỏi Vim mà không lưu thay đổi (tương tự như :quit!).
            - `:wq:` Lưu và thoát khỏi Vim (tương tự như :writequit).
            - `:x:` Lưu và thoát khỏi Vim (tương tự như :writequit, nhưng chỉ lưu khi có sự thay đổi).
            - `:e [filename]:` Mở một tập tin mới trong Vim.
            - `:set [option]:` Thiết lập các tùy chọn Vim (ví dụ: :set number để hiển thị số dòng).
            - `:s/search/replace/g:` Tìm kiếm và thay thế trong tài liệu (ví dụ: :s/old/new/g).
            - `:vsplit [filename]:` Mở một tập tin mới trong cửa sổ phụ dọc.
# Tổ hợp phím 

`Ctrl + R:` tìm kiếm câu lệnh đã dùng trong quá khứ

`Ctrl + S:`
- Chức năng: Dừng xuất ra màn hình (tạm thời tạm dừng).

>Thông thường, khi bạn nhấn Ctrl + S trên bàn phím trong khi đọc hoặc ghi dữ liệu trên một terminal, dữ liệu sẽ bị đóng băng. Điều này có nghĩa là không có thêm dữ liệu nào sẽ được hiển thị trên màn hình cho đến khi bạn nhấn Ctrl + Q để tiếp tục.

`Ctrl + G:`
- Chức năng: Phát ra một tiếng bíp.

>Thường được sử dụng khi cần chú ý hoặc cảnh báo người dùng, đặc biệt trong các trường hợp như lỗi hoặc sự kiện quan trọng trong quá trình thực thi một chương trình hoặc lệnh.

# Khái niệm và 3 loại streams: 
- `Standard input:` dữ liệu đầu vào mà ng dùng nhập

- `Standard output:` dữ liệu đầu ra là kết quả của dữ liệu đầu vào

- `Standard error:` dữ liệu đầu ra bị lỗi(thông tin đầu ra lỗi)

# Managing Files and Link: ‘ls’, ‘cp’, ‘mv’, ‘rm’, ‘touch’, ‘ln’**

- `ls:` Liệt kê các tập tin và thư muc trong thư mục hiện tại
  `-l:` hiển thị chi tiết
  `-a:` hiển thị cả các file ẩn
  `-h:` hiển thị kích thước tập tin dễ đọc

- `cd:` Di chuyển qua lại giữa các thư mục để làm việc

- `cp:` Sao chép tập tin
  `-r:` sap chép toàn bộ thư mục

- `mv:` Di chuyển tập tin từ chỗ này sang chỗ khác để làm viêc. Ngoài ra có thể dùng mv để đổi tên tập tin.

- `rm:` Xóa thư muc
  -`r:` Xóa toàn bộ thư mục

- `touch:` Tạo file mới 
- `ln:` tạo liên kết link giữa các tập tin hoặc thư mục
  - Có hai loại liên kết chính: liên kết cứng (hard link) và liên kết mềm (symbolic link).
    - `-s` hoặc --symbolic: Tạo một liên kết mềm (symbolic link) thay vì một liên kết cứng (hard link).
    - `-f` hoặc --force: Ghi đè lên liên kết hiện có nếu nó đã tồn tại.
    - `-i` hoặc --interactive: Yêu cầu xác nhận từ người dùng trước khi ghi đè lên liên kết hiện có.
    - `-r :` tạo liên kết cứng với thư mục

# Managing File Ownership: ‘chown’, ‘chgrp’

- Trong Linux, `chown và chgrp` là hai lệnh được sử dụng để thay đổi quyền sở hữu và nhóm sở hữu của tập tin và thư mục.

- `chown:` Dùng để thay đổi quyền chủ sở hữu của 1 tập tin hoặc thư mục.
  ````
  vd: chown user1:group1 file1.txt
  ````
- `chgrp:` Dùng để thay đổi nhóm nhở hữa của 1 tập tin hoặc thư mục
  ```
  vd: chgrp group2 file2.txt
  ```
# Controlling Access to Files: Understanding Permissions, ‘chmod’

- `chmod:` được sử dụng để thay đổi quyền truy cập của các tập tin và thư mục. 
- `Quyền truy cập` ở đây bao gồm quyền đọc (read), quyền ghi (write), và quyền thực thi (execute) đối với các tập tin và thư mục.
  ```
  vd: chmod u+rwx,g+rx,o+r file1.txt
  ```
  Trong đó: 
  - u là owner (chủ sở hữu), 
  - g là group (nhóm), 
  - o là others (người dùng khác), 
  - + là thêm quyền, 
  - - là loại bỏ quyền, 
  - và r, w, x lần lượt là quyền đọc, ghi, thực thi.

**Các tùy chọn**
- -R hoặc --recursive: Thực hiện thay đổi quyền truy cập đệ quy cho toàn bộ cây thư mục.
- -v hoặc --verbose: Hiển thị thông báo chi tiết về các thay đổi đã được thực hiện.
- -c hoặc --changes: Chỉ hiển thị thông báo khi có thay đổi.

**Phân quyền cho 1 user chỉ đọc 1 thư mục**
```
chmod u=r file.txt
```

**Tools for Locating Files: ‘find’, ‘locate’, ‘whereis’, ‘which’**

***Dưới đây là các công cụ phổ biến để tìm kiếm tệp trong hệ điều hành Linux, mỗi công cụ có một cách tiếp cận khác nhau:***

- `find:` được sử dụng để tìm kiếm tệp dựa trên các tiêu chí như tên tệp, loại tệp, kích thước và nhiều thuộc tính khác

  ```
  find /đường/dẫn -name "tên_tệp"
  ```

- `locate:` sử dụng cơ sở dữ liệu tìm kiếm nhanh để tìm kiếm tệp

  ```
  locate tên_tệp
  ```

- `whereis:` sử dụng để tìm kiếm các tệp thực thi, mã nguồn và tài liệu liên quan đến một chương trình đã được cài đặt.

  ```
  whereis tên_chương_trình
  ```

- `which:` sẽ chỉ ra đường dẫn của tệp thực thi của một lệnh được gọi từ dòng lệnh. Nó sẽ tìm kiếm trong các thư mục được liệt kê trong biến môi trường PATH.

  ```
  which tên_lệnh
  ```

# Managing Users and Groups

**Để thực hành tạo và sửa đổi người dùng và nhóm trong hệ điều hành Linux, bạn có thể sử dụng các lệnh sau:**

**Tạo người dùng mới:**

- Sử dụng lệnh adduser hoặc useradd:

  ```
  sudo adduser username  // ko có tk login

  or

  sudo useradd username  // có tk login
  ```
  Thay username bằng tên của người dùng mới.

- Để thêm người dùng vào group cụ thể, sử dụng lệnh usermod:

  ```
  sudo usermod -aG groupname username
  ```

- Để gỡ username ra khỏi group
  ```
  sudo gpasswd -d truongpv root
  ```
  Thay `groupname` bằng tên của nhóm và `username` bằng tên của người dùng.

**Tạo nhóm mới:**

- Sử dụng lệnh addgroup hoặc groupadd:

  ```
  sudo addgroup groupname  //nếu bạn đang sử dụng một hệ điều 
                            hành dựa trên Debian và muốn có một lệnh 
                            đơn giản và dễ sử dụng hơn.
  or

  sudo groupadd groupname  // khi bạn cần kiểm soát chi tiết hơn về 
                            các thiết lập nhóm.
  ```
  Thay groupname bằng tên của nhóm mới.

**Sửa đổi người dùng và nhóm:**

- Để sửa đổi thông tin người dùng, bạn có thể sử dụng lệnh usermod:

  ```
  sudo usermod [tùy chọn] username

  or

  sudo usermod -l new_username old_username
  ```

- Để sửa đổi thông tin nhóm, bạn có thể sử dụng lệnh groupmod:

  ```
  sudo groupmod [tùy chọn] groupname

  or

  sudo groupmod -n new_groupname old_groupname
  ```

- Để xóa người dùng hoặc nhóm, bạn có thể sử dụng lệnh deluser hoặc userdel để người dùng và delgroup hoặc groupdel để nhóm.

  ```
  sudo deluser username  // xóa username

  or

  sudo delgroup groupname  // xóa groupname
  ```


