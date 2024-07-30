## Các Lệnh cơ bản trong linux

- `cd`: di chuyển đến các thư mục
- `pwd`: Xem thư mục đang làm việc
- `man`: Để tra cứu
- `cat`: Để  hiển thị nội dung các file tệp tin
- `tac`: Để  hiển thị nội dung các file tệp tin từ dưới lên
- `sort`: Sắp xếp nội dung của các tệp tin theo thứ tự được chỉ định.
- `split`: chia file nội dung tệp tin
- `uniq`: Loại bỏ từ trùng lặp trong file tệp tin.
- `nl`: đánh số thứ tự trong file tệp tin
- `head`: Hiện thị 10 dòng đầu trong file tệp tin.
- `tail`: Hiển thị 10 dòng cuối trong file tệp tin.
- `less`: Hiển thị nội dùng trang một cách trang trọng, cho phép bạn di chuyển lên và xuống, và ngay cả sang trái và phải (nếu nội dung quá dài).
- `cut`: Để cắt và trích xuất các phần của dòng văn bản từ một tập tin hoặc đầu vào được cung cấp.
- `wc`: sử dụng để đếm số lượng dòng, từ và byte trong một tệp tin hoặc đầu vào được cung cấp.

    **Một số tùy chọn phổ biến được sử dụng với lệnh wc:**
  - wc -l: Đếm số lượng dòng.

  - wc -w: Đếm số lượng từ.

  - wc -c: Đếm số lượng byte.

- `grep`: được sử dụng để tìm kiếm mẫu văn bản trong các tệp tin hoặc đầu vào được cung cấp, và hiển thị các dòng chứa mẫu đó.

    > CP: grep [tùy_chọn] [mẫu] [tập_tin]

    **Một số tùy chọn phổ biến của grep bao gồm:**

  - grep -i: Không phân biệt chữ hoa và chữ thường.

    `VD: grep -i "error" file.txt` tìm kiếm từ "error" trong file.txt

  - grep -r: Tìm kiếm đệ quy trong các thư mục con.

    `VD: grep -r "error"`

  - grep -n: Hiển thị số dòng của mỗi kết quả.

    `grep -n "error" file.txt`

  - grep -v: In ra các dòng không chứa mẫu.

- `sed`: là một công cụ mạnh mẽ được sử dụng để thay đổi và xử lý văn bản trong các luồng dữ liệu hoặc tệp tin.

    > CP: sed [tùy_chọn] 'lệnh' [tập_tin]

    **Một số tùy chọn phổ biến của sed bao gồm:**

  - sed -e: Cho phép sử dụng nhiều lệnh sed liên tiếp.

  - sed -i: Sửa đổi trực tiếp tập tin đầu vào (thay đổi nội dung của tệp).

  - sed -n: Không in ra dòng mặc định, chỉ in ra dòng đã được yêu cầu.

  - sed -r hoặc sed -E: Sử dụng biểu thức chính quy mở rộng (regular expressions).

    **Ví dụ cách sử dụng sed:**

    1. Thay thế tất cả các lần xuất hiện của một chuỗi trong một tập tin:
    - `sed 's/old_string/new_string/g' file.txt`
    2. Xóa dòng trống từ một tập tin:
    - `sed '/^$/d' file.txt`
    3. Thêm một dòng mới vào cuối mỗi dòng trong tệp tin:
    - `sed 's/$/ new_text/' file.txt`
    4. Xóa dòng cuối cùng của một tệp tin:
    - `sed '$d' file.txt`

- `awk`: là một công cụ mạnh mẽ và linh hoạt được sử dụng trong hệ điều hành Linux và các hệ điều hành tương tự Unix để xử lý và phân tích dữ liệu trong các tệp tin văn bản.
  - `awk` hoạt động dựa trên các quy tắc và hành động được xác định bởi người dùng, giúp bạn tìm kiếm, trích xuất, và xử lý dữ liệu từ các tệp tin văn bản một cách linh hoạt.

    > CP: awk 'pattern {action}' [tập_tin]

    **Trong đó:**

  - `pattern`: Là một biểu thức điều kiện để lọc các dòng từ đầu vào. Nếu dòng thỏa mãn điều kiện, hành động sẽ được thực thi trên dòng đó.
  - `{action}`: Hành động sẽ được thực thi nếu một dòng thỏa mãn điều kiện. Hành động này có thể là in dòng, tính toán, hoặc xử lý dữ liệu theo cách tùy ý.

    **Một số ví dụ về cách sử dụng awk:**
    1. In ra tất cả các dòng trong tệp tin:
    - `awk '{print}' file.txt`
    2. In ra cột thứ hai từ mỗi dòng trong tệp tin (giả sử cột được phân tách bằng dấu phẩy):
    - `awk -F ',' '{print $2}' file.txt`
    3. Tính tổng của cột thứ ba từ mỗi dòng trong tệp tin:
    - `awk -F ',' '{sum += $3} END {print sum}' file.txt`
    4. In ra các dòng có độ dài lớn hơn 10 ký tự:
    - `awk 'length($0) > 10' file.txt`

- `kill`: được sử dụng để gửi một tín hiệu (signal) đến một tiến trình cụ thể, yêu cầu tiến trình đó kết thúc hoặc thực hiện một hành động nhất định.

  *CP: lệnh kill là:*

      kill [OPTIONS] <pid>

  Trong đó:

  - pid là Process ID (ID của tiến trình) của tiến trình mà bạn muốn gửi tín hiệu đến.
  Một số tùy chọn thường được sử dụng với lệnh kill bao gồm:

  - `kill -9`hoặc `--signal=SIGKILL`: Gửi tín hiệu KILL, làm cho tiến trình bị chấm dứt ngay lập tức mà không cần thực hiện bất kỳ công việc dọn dẹp nào.
  - `kill -15` hoặc `--signal=SIGTERM`: Gửi tín hiệu TERM, làm cho tiến trình chấm dứt một cách bình thường, cho phép nó thực hiện các công việc dọn dẹp trước khi kết thúc

  **Ví dụ:**

  - kill 1234: Gửi tín hiệu TERM đến tiến trình có PID là 1234.

  - kill -9 5678: Gửi tín hiệu KILL đến tiến trình có PID là 5678

>Lưu ý rằng bạn cần có quyền để gửi tín hiệu cho một tiến trình, vì vậy thường bạn sẽ cần chạy lệnh `kill` với quyền root (bằng cách thêm `sudo` vào trước lệnh).
Tuy nhiên, bạn chỉ nên sử dụng tín hiệu `KILL (-9)` khi cần thiết, vì nó không cho phép tiến trình thực hiện các công việc dọn dẹp trước khi kết thúc và có thể gây ra sự mất mát dữ liệu hoặc trạng thái không như mong đợi.

| Lệnh     | Mô tả                                       | tác dụng        | 
| :--------| :-------------------------------------------| :-------------- | 
| kill     | Gửi tín hiệu TERM (terminate) đến tiến trình|- Tiến trình được yêu cầu kết thúc bình thường và có thể thực hiện các công việc dọn dẹp trước khi kết thúc.<br>- Tiến trình có thể bắt tín hiệu này và thực hiện các hành động cần thiết trước khi kết thúc.| 
| kill -9 hoặc kill -SIGKILL   | Gửi tín hiệu KILL đến tiến trình          | - Tiến trình bị chấm dứt ngay lập tức mà không có cơ hội thực hiện bất kỳ công việc dọn dẹp nào.<br>- Không có tùy chọn cho tiến trình để "ngắt" hay "từ chối" tín hiệu KILL này.        | 

- `apt-get`: công cuj quản lý gói phầm mềm

- `dpkg --get-selections`: Check list phần mềm đã cài đặt

- `dpkg -l | grep <tên-phần-mềm>`: check 1 phần mềm đã được cài đặt

- `apt-update`: là việc cập nhật danh sách các gói phần mềm từ các nguồn cài đặt trên hệ thống của bạn

- `apt-upgrade`: Thực hiện việc cài đặt các gói phần mềm mới nhất từ các kho lưu trữ đã được cập nhật bởi lệnh `apt update`

  **Khi nào dùng apt update:**

  - Khi bạn muốn cập nhật thông tin về các gói phần mềm từ các kho lưu trữ.

  - Trước khi chạy apt upgrade, để đảm bảo rằng bạn đang cập nhật từ các nguồn dữ liệu mới nhất.

  **Khi nào dùng apt upgrade:**

  - Khi bạn muốn cài đặt phiên bản mới nhất của các gói phần mềm đã được cập nhật.

  - Thường được chạy sau khi apt update để cập nhật các gói phần mềm trên hệ thống của bạn.

- `ls`: hiển thị danh sách thư mục đang đứng
- `cp`: Copy file or thư mục , đổi tên thư mục
- `mv`: di chuyển file ỏr thư mục, đổi tên thư mục
- `rm`: xóa thư mục rỗng
- `touch`: tạo file
- `ln`: tạo các liên kết (links) giữa các tệp tin hoặc thư mục.

  - Liên kết cứng (hard link):
  Liên kết cứng tạo ra một liên kết giữa tên file và inode, làm cho file trở nên có nhiều tên. Khi bạn xóa một tên file, dữ liệu vẫn tồn tại trên đĩa nếu có ít nhất một liên kết khác đến inode đó
    ```
    CP: ln source_file hard_link
    ```
    **Ví dụ:**
    Giả sử chúng ta có một file file1.txt, và chúng ta muốn tạo một liên kết cứng tên là hard_link.txt đến file này:
    ```
    ln file1.txt hard_link.txt
    ```
  - Liên kết mềm (symbolic link):
  Liên kết mềm tạo ra một liên kết tới tên file, không phải inode. Khi file gốc bị xóa, liên kết mềm sẽ trở thành "broken" và không thể truy cập nữa.
    ```
    CP: ln -s source_file symbolic_link
    ```
    **Ví dụ:**
    Giả sử chúng ta muốn tạo một liên kết mềm có tên là soft_link.txt đến file file1.txt:
    ```
    ln -s file1.txt soft_link.txt
    ```

    **Lưu ý:**
    - Liên kết cứng chỉ hoạt động trong phạm vi cùng một filesystem.
    - Liên kết mềm có thể trỏ đến file ở một filesystem khác.
    - Dấu -s là tùy chọn dùng để chỉ định rằng chúng ta muốn tạo một liên kết mềm.
    - Đường dẫn có thể là tuyệt đối hoặc tương đối đối với vị trí hiện tại.
    - Sau khi thực hiện lệnh ln, bạn sẽ thấy liên kết đã được tạo trong thư mục hiện taị
