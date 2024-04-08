# Running Job in the Future: ‘cron’, ‘at’

## Cron là gì?

- `Crontab` là một cách để tạo và chạy các lệnh theo một chu kỳ xác định. Đây là tiện ích giúp lập lịch trình để chạy những dòng lệnh bên phía server, nhằm thực thi một hoặc nhiều công việc nào đó theo thời gian được lập sẵn.

## Crontab làm việc như thế nào?

- Một cron schedule đơn giản là một text file. Mỗi người dùng có một cron schedule riêng, file này thường nằm ở `/var/spool/cron`. `Crontab files` không cho phép bạn tạo hoặc chỉnh sửa trực tiếp với bất kỳ trình text editor nào, trừ phi bạn dùng lệnh crontab.

**Một số lệnh thường dùng:**
```
crontab -e: tạo hoặc chỉnh sửa file crontab 

crontab -l: hiển thị file crontab 

crontab -r: xóa file crontab
```

## Cách sử dụng Crontab Linux

- Cron hoạt động dựa trên các lệnh được chỉ định trong cron table (crontab). Mỗi người dùng, kể cả root, đều có thể có một file cron. Các file này theo mặc định sẽ không tồn tại. Nhưng ta có thể tạo nó trong thư mục /var/spool/cron bằng cách dùng lệnh crontab -e. 
- Ngoài ra, lệnh này cũng có thể được dùng để chỉnh sửa một file cron. Chúng tôi khuyên bạn không nên các sử dụng trình editor tiêu chuẩn (như Vi, Vim, Emacs, Nano,…). Bởi vì sử dụng lệnh crontab không chỉ cho phép bạn chỉnh sửa lệnh, nó còn khởi động lại crond daemon khi ta lưu và thoát trình editor. Lệnh crontab sử dụng Vi làm editor cơ bản của nó, vì Vi luôn luôn khả dụng.

- Các file cron sẽ trống, nên các lệnh phải được thêm từ đầu. 

**Dưới đây là một ví dụ về định nghĩa các công việc trong file cron:**

```
# crontab -e
SHELL=/bin/bash
MAILTO=root@example.com
PATH=/bin:/sbin:/usr/bin:/usr/sbin:/usr/local/bin:/usr/local/sbin

# For details see man 4 crontabs

# Example of job definition:
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  * user-name  command to be executed

# backup using the rsbu program to the internal 4TB HDD and then 4TB external
01 01 * * * /usr/local/bin/rsbu -vbd1 ; /usr/local/bin/rsbu -vbd2

# Set the hardware clock to keep it in sync with the more accurate system clock
03 05 * * * /sbin/hwclock --systohc

# Perform monthly updates on the first of the month
# 25 04 1 * * /usr/bin/dnf -y update
```

Để thiết lập một công việc trong cron, bạn cần chỉnh sửa hoặc tạo một tệp cấu hình cron, thường được gọi là "crontab".

**Dưới đây là cách để thiết lập một công việc trong cron:**

1. Mở terminal hoặc SSH vào hệ thống Unix/Linux của bạn.

2. Sử dụng lệnh sau để mở crontab để chỉnh sửa:

   ```
   crontab -e
   ```

   Nếu bạn làm điều này lần đầu tiên, hệ thống có thể hỏi bạn chọn trình soạn thảo mặc định. Bạn có thể chọn trình soạn thảo mà bạn thích như `nano`, `vim`, hoặc `emacs`.

3. Một lần mở, bạn sẽ thấy một trình soạn thảo mở với tệp crontab. Mỗi dòng trong tệp này tương ứng với một công việc được lên lịch trong cron.

4. Để thêm một công việc mới, bạn cần thêm một dòng mới vào cuối tệp crontab với cú pháp sau:

   ```
   * * * * * /path/to/command
   ```

   Trong đó:
   - Năm dấu * đầu tiên đại diện cho phút (0-59).
   - Dấu * thứ hai đại diện cho giờ (0-23).
   - Dấu * thứ ba đại diện cho ngày trong tháng (1-31).
   - Dấu * thứ tư đại diện cho tháng (1-12).
   - Dấu * thứ năm đại diện cho ngày trong tuần (0-6, 0 là Chủ Nhật).
   - `/path/to/command` là đường dẫn đến lệnh hoặc script bạn muốn chạy.

   Ví dụ, nếu bạn muốn chạy một script mỗi ngày lúc 2 giờ sáng, bạn có thể thêm dòng sau vào crontab:

   ```
   0 2 * * * /path/to/your_script.sh
   ```

5. Sau khi bạn đã thêm hoặc sửa đổi các công việc cần thiết, lưu và đóng tệp crontab. 

   Trong `nano`, bạn có thể nhấn `Ctrl + X` để thoát, sau đó trả lời "Y" để lưu thay đổi và nhấn Enter để xác nhận.

6. Crontab sẽ tự động lưu và kích hoạt các thay đổi. Các công việc sẽ được thực thi theo lịch trình bạn đã chỉ định.

Lưu ý rằng bạn cần có quyền truy cập crontab để thực hiện các thay đổi này, vì vậy đảm bảo bạn có quyền hạn cần thiết trước khi cố gắng chỉnh sửa crontab.

## Khi nào có nhu cầu sử dụng cron ?

Cron được sử dụng khi bạn cần thực hiện các tác vụ tự động theo lịch trình định kỳ. 

**Dưới đây là một số trường hợp phổ biến khi bạn có thể cần sử dụng cron:**

1. **Sao lưu dữ liệu định kỳ**: Bạn có thể sử dụng cron để lên lịch sao lưu dữ liệu từ máy chủ hoặc hệ thống của bạn vào một vị trí lưu trữ khác, như một máy chủ sao lưu hoặc dịch vụ lưu trữ đám mây. Việc sao lưu dữ liệu định kỳ giúp đảm bảo rằng bạn không mất dữ liệu quan trọng nếu xảy ra sự cố.

2. **Chạy các tác vụ hệ thống định kỳ**: Cron có thể được sử dụng để chạy các tác vụ hệ thống tự động như quét và làm sạch các tệp hệ thống, cập nhật cơ sở dữ liệu, gửi báo cáo tự động, kiểm tra các dịch vụ hoạt động, vv.

3. **Quản lý tài nguyên hệ thống**: Bằng cách lên lịch các tác vụ như kiểm tra sức khỏe hệ thống, xóa các tệp không cần thiết, hoặc tự động khởi động lại hệ thống, cron có thể giúp bạn duy trì tài nguyên hệ thống một cách hiệu quả.

4. **Thực hiện các tác vụ tự động cho ứng dụng**: Nếu bạn có một ứng dụng hoặc dịch vụ cần thực hiện các tác vụ như gửi email hàng ngày, xử lý hàng đợi công việc, hoặc cập nhật dữ liệu từ nguồn bên ngoài, cron có thể giúp bạn tự động hóa các tác vụ này.

5. **Lên lịch cho các bản cập nhật hệ thống và ứng dụng**: Cron có thể được sử dụng để tự động cập nhật hệ thống hoặc ứng dụng vào thời điểm phù hợp, giúp giảm thiểu tác động đến sự hoạt động của hệ thống hoặc ứng dụng.

Tóm lại, khi bạn cần thực hiện các tác vụ định kỳ mà không muốn phải thực hiện chúng thủ công mỗi lần, bạn có thể sử dụng cron để tự động hóa các công việc đó.

## Thiết lập 1 job chạy vào 2 giờ sáng mỗi ngày

- Dùng lệnh `crontab -e`

thêm dòng này vô cuối:
```
0 2 * * * /path/to/your_command_or_script
```
## Thiết lập 1 job chạy vào 3 giờ, 2 ngày 1 lần.

- Dùng lệnh `crontab -e`

thêm dòng này vô cuối:

```
0 3 */2 * * /path/to/your_command_or_script
```
