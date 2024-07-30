# Tiến trình trong Linux ( Linux Process )

## Linux process

- Một **process** ( tiến trình ) là tập hợp của một hay nhiều tác vụ ( threads) liên quan chạy  tại cùng một thời điểm
trên cùng một máy. 
	- Một tiến trình lỗi có thể có hoặc không ảnh hưởng đến các tiến trình khác đang chạy trong hệ thống.
	- Các tiến trình sử dụng rất nhiều nguồn tài nguyên của máy như bộ nhớ, RAM, CPU và các thiết bị ngoại vi như máy in,
	màn hình..
	- Hệ điều hành ( kernel ) có nhiệm vụ phân bổ các nguồn tài nguyên cho các **process** sao cho hợp lí để tối ưu hóa
	sức mạnh máy tính.

- Cửa sổ dòng lệnh ( terminal window ) là một tiến trình cho phép người dùng thực thi các chương trình, truy cập vào
các nguồn tài nguyên, chạy các ứng dụng ngầm... bằng các dòng lệnh.

- Các tiến trình (process) có thể khác nhau  tùy thuộc vào nhiệm vụ mà nó thực hiện :

|Loại tiến trình|Mô tả|
|--------|---------|
|Interactive |Người dùng phải khởi động  bằng lệnh hay qua giao diện|
|Batch |Các tiến trình tự động chạy được đặt lịch từ dòng lệnh và sau khi chạy xong tự động tắt liên kết dến terminal|
|Daemons|Các tiến trình trên máy chủ chạy liên tục. Có nhiều tiến trình được bật khi hệ thống khởi động, và đợi cho đến khi có yêu cầu truy cập đến|
|Threads|Các tác vụ con của một tiến trình cha, chia sẻ tài nguyên và bộ nhớ RAM với nhau và được đặt kế hoạch và điều hành bởi hệ thống trên cơ sở cá nhân|
|Kernel Threads|Các tác vụ trong kernel mà người dùng có thể khởi động hay tắt nó đi. Ví dụ user có thể chuyển một tác vụ từ CPU nay sag CPU khác, hoặc đảm bảo rằng hoạt động i/o trên 1 đĩa cứng đã hoàn thành|

- Khi một tiến trình đang chạy, có nghĩa rằng nó đang thực thi các bước xử lí trên CPU hoặc nó đang đợi sự chia sẻ tài nguyên để chạy.
	-  Một **scheduler** ( kế hoạch theo lịch trình ) liên tục thay đổi các processes vào hoặc ra ngoài CPU, thời gian chia sẻ dựa trên mức độ
	ưu tiên, bao nhiêu thời gian cần và bao nhiêu thời gian đã cấp cho một tác vụ.
	- Tất cả các tiến trình trên đều nằm trên các hàng đợi ( runq queue) trên các CPUs. Đôi khi các tiến trình sẽ ở trạng thái ngủ 
(**sleep state**) khi chúng đang chờ một hoạt động nào đó xảy ra trước rồi mới chạy, ví dụ như đợi người dùng viết gì đó, có tiến trình đưa ra gợi ý cho từ tiếp theo. 
Trong trường hợp đó, process sẽ đặt trong một hàng đợi ( queue )
	- Có những tiến trình không chạy đều thường xuyên, đôi khi có một chương trình con đã hoàn thành tác vụ nhưng chương trình cha không quan tâm đến nó đã kết thúc
	hay chưa mà chỉ quan tâm đến kết quả được tạo ra từ nó. Những tiến trình đó ở trạng thái **zombie** - nghĩa là tuy nó đã kết thúc nhưng 
	vẫn được biểu diễn trên danh sách tiến trình hệ thống. 
	
- Tại một thời điểm, luôn có rất nhiều tiến trình đang được thực thi. Hệ thống kiểm soát chúng bằng cách đặt cho chúng các chỉ sổ riêng biệt, gọi là
**Process ID** ( PID ) 
	- Mỗi PID là duy nhất tại thời điểm đó
	- PID dùng dể kiểm soát trạng thái của tiến trình, mức độ sử dụng CPU, RAM, xác định tài nguyên được đặt ở đâu trên bộ nhớ và các đặc tính khác nữa.
	- Các PID mới sẽ được sắp xếp theo mức độ tăng dần mỗi khi các tác vụ mới hình thành. PID 1 là tiến trình đầu tiên (**init process**)
	và các **tiến trình thành công** ( succeeding process) được đánh dấu với số cao hơn.

- Tại một thời điểm có rất nhiều tiến trình cùng chạy trên hệ thống, tuy nhiên **CPU** chỉ có thể xử lí 1 tác vụ tại một thời điểm.
	- Linux cho phép bạn cài đặt mức độ ưu tiên (**priority**) cho các processes. Priority cho một process có thể được đặt bằng một giá trị **niceness** đặc biệt.
	Giá trị **niceness** càng thấp chỉ sổ **priority** càng cao.
	- Process nào có mức độ priority cao hơn sẽ có thời gian sử lí nhiều hơn, ưu tiên cho các processes có priority thấp hơn xử lí trước.
	- Trong Linux, giá trị `niceness` (NI) **cao nhất** là `-20` , **thấp nhất** là `19`. `Priority` = `20` + `NI`
	
	+  Bạn có thể xem chương trình nào đang chạy với một giá trị priority cụ thể :
	`nice -n nice_value program_name `
	- Bạn có thể gán các giá trị real-time priority cho các tác vụ quan trọng và nhạy cảm như kiểm soát máy hoặc thu thập thông tin từ dữ liệu đầu vào.
	+ Bạn có thể thay đổi priority của một tiến trình đang chạy :
	`renice -n nice_value -p process_id` | ví dụ : `nice -n 10 5560` hoặc `nice -n 10 firefox`  
	

## Running processes 

### 1. Sử dụng thành thạo và đọc hiểu các thông số về CPU, RAM, quản lý các tiến trình (process)

> Để sử dụng thành thạo và đọc hiểu các thông số về CPU, RAM và quản lý các tiến trình trên hệ thống Linux, bạn có thể sử dụng các công cụ như htop, top, và các lệnh dòng lệnh khác như ps

**Dưới đây là một số điều bạn cần biết:**

### 1.1. Thông tin về CPU:

- Usage (Sử dụng): Phần trăm tài nguyên CPU đang được sử dụng. Đối với htop hoặc top, nó được hiển thị ở góc trên bên phải.

- Load Average (Trung bình tải): Số lượng tiến trình đang chờ xử lý bởi CPU. Trong htop, nó được hiển thị ở phía trên cùng.

- Process List (Danh sách tiến trình): Danh sách các tiến trình đang chạy, bao gồm thông tin về CPU sử dụng của từng tiến trình.

### 1.2. Thông tin về RAM:

- Total (Tổng): Tổng dung lượng RAM trên hệ thống.

- Used (Đã sử dụng): Dung lượng RAM đã được sử dụng.

- Free (Trống): Dung lượng RAM còn trống.

- Buffers/Cached (Bộ nhớ đệm/Đã cache): Dung lượng RAM được sử dụng cho việc lưu trữ dữ liệu tạm thời và được cache để tăng tốc độ truy cập.

### 1.3. Quản lý các tiến trình:
```
- Process ID (PID): ID duy nhất của tiến trình.

- User (Người dùng): Tên người dùng sở hữu tiến trình.

- %CPU (Phần trăm CPU): Phần trăm tài nguyên CPU được tiến trình sử dụng.

- %MEM (Phần trăm RAM): Phần trăm tài nguyên RAM được tiến trình sử dụng.
```

### 1.4. Một số lệnh cần biết:

- `htop`: Hiển thị thông tin về CPU, RAM và quản lý tiến trình trong một giao diện dễ đọc.

- `top`: Hiển thị thông tin tương tự như htop, nhưng trong một giao diện text-based đơn giản hơn.

- `ps`: Hiển thị danh sách các tiến trình đang chạy cùng với thông tin chi tiết về từng tiến trình.

### 2.  Lệnh ps

Lệnh `ps` hiển thị thông tin về các tiến trình đang chạy, định danh bởi **PID**

```
root@ubuntu:~# ps
   PID TTY          TIME CMD
  2850 pts/0    00:00:00 bash
  2865 pts/0    00:00:00 ps
```
- Lệnh `ps` có nhiều lựa chọn để xác định chính xác nhiệm vụ cần kiểm tra, thông tin nào để hiển thị về chúng, 
và chính xác định dạng đầu ra nên được sử dụng.
	
	- `ps -u` biểu thị các tiến trình đang chạy cho một user cụ thể 
	```
	# ps -u songle
	 PID TTY          TIME CMD
	 847 ?        00:00:00 sshd
	 848 pts/2    00:00:00 bash
	1070 ?        00:00:00 sshd
	1071 pts/3    00:00:00 bash
	6475 pts/3    00:00:00 top
	```
	- Lệnh `ps -ef` hiển thị toàn bộ các quy trình trong hệ thống. Lệnh `ps -eLf` đi xa hơn một bước và hiển thị một dòng thông tin 
	cho mỗi luồng (một quy trình có thể chứa nhiều luồng).

### 3. Lệnh top

Lệnh `top` sẽ show ra các thông tin cần thiết để người quản trị giám sát được các thông số, CPU, RAM, I/O ,
các tiến trình đang hoạt động trên hệ thống.
	
![Imgur](https://i.imgur.com/axxWTJB.jpg)
	
- Dòng dầu tiên : 
	+ Thời gian hệ thống được bật lên
	+ Số người đang đăng nhập vào hệ thống
	+ Trung bình tải của hệ thống ( load average )
		
	- **Load average** xác định hệ thống đang làm việc ở mức độ nào . 
	+ 1.00 per CPU : CPU đang làm việc 100% nhưng chưa bị quá tải
	+ 1.00 per CPU : hệ thống đang gặp vấn đề, một số processes đang trong tình trạng không phản hồi (non-responding)
		hay còn gọi là **runaway** process.
		
- Dòng thứ 2 : 
	+ Tổng số processes, số process đang chạy, sleeping, stopped và zombie process.
	+ So sánh số tiến trình đang chạy với mức tải trung bình giúp xác định xem hệ thống đã đạt đến dung lượng của nó hoặc có thể một người dùng cụ thể đang chạy quá nhiều tiến trình.
	Các stopped processes phải được kiểm tra để xem mọi thứ có đang chạy đúng hay không.

- Dòng thứ 3 :
	+ Thời gian được chia giữa người dùng (us) và kernel (sy) bằng số % thời gian của CPU cho cả 2.
	+ % của công việc người dùng ở mức priority thấp ( ni )
	+ Idle mode (id) 
	+ % công việc đang nằm trên hàng đợi cho I/O
	+ % sự gián đoạn của phần cứng (hi ) với phần mềm (si)
	+ Thời gian lãng phí steal time (st) thường dùng cho máy ảo, cái mà một số tiến trình chạy trên CPU cho những mục đích khác.
	
	
- Dòng thứ 4 và 5 : thông tin bộ nhớ đã sử dụng gồm toàn bộ dung lượng, dung lượng đã dùng, dung lượng trống :

	+ Physical memory ( RAM ) - dòng 4
	+ Swap space - dòng 5
	
	- Khi RAM hết, hệ thống sẽ tiến hành sử dụng swap space để bổ sung dung lượng cho RAM.
	
![Imgur](https://i.imgur.com/IeNcFtX.jpg)
	
![Imgur](https://i.imgur.com/4dcVIJx.jpg)
	
	- 
	
- Ngoài `top`, `htop` và `atop` cũng là 2 lệnh chỉ ra các thông số chi tiết tiến trình đang chạy của hệ thống . Tuy nhiên bạn cần cài đặt thêm vào bằng lệnh :
` apt install htop`

### Lệnh htop

- `htop` là một công cụ dòng lệnh được sử dụng để hiển thị thông tin chi tiết về tài nguyên hệ thống trên hệ điều hành Linux. Nó cung cấp một giao diện dễ đọc và dễ sử dụng hơn so với công cụ tương tự là top, cho phép người dùng theo dõi và quản lý tài nguyên hệ thống một cách hiệu quả.

**Cách sử dụng htop trong Linux:**

1. Mở Terminal: Mở terminal trên hệ điều hành Linux của bạn. Bạn có thể sử dụng tổ hợp phím `Ctrl + Alt + T` trên nhiều phân phối Linux để mở terminal.

2. Gõ Lệnh htop: Gõ lệnh sau vào terminal và nhấn Enter: `htop`

3. Dùng htop để Xem Thông Tin Hệ Thống:

   - Khi `htop` khởi chạy, bạn sẽ thấy một giao diện đồ họa với danh sách các tiến trình đang chạy, cùng với các thông tin chi tiết như CPU, RAM, Swap và các chỉ số khác.
   - Bạn có thể sử dụng các phím mũi tên (lên, xuống, trái, phải) để di chuyển giữa các tiến trình.
   - Để tắt một tiến trình, bạn có thể nhấn phím `F9,` chọn lựa chọn tương ứng và nhấn Enter.
   - Để sắp xếp các tiến trình theo một chỉ số cụ thể, nhấn các phím tương ứng với các chỉ số đó (ví dụ: `F6` để sắp xếp theo CPU).
   - Để thoát khỏi `htop`, bạn có thể nhấn phím `F10`hoặc `Ctrl + C`.

>`htop` cung cấp một cách thuận tiện và trực quan để theo dõi và quản lý tài nguyên hệ thống trên Linux, giúp bạn hiểu rõ hơn về hiệu suất và hoạt động của máy tính của mình.

## pid của 1 process

- Để tìm PID (Process ID) của một tiến trình trên hệ thống Linux, bạn có thể sử dụng lệnh pgrep hoặc pidof, hoặc kết hợp sử dụng ps và grep. 

Dưới đây là cách thực hiện bằng mỗi phương pháp:

**Sử dụng pgrep:**

    `pgrep <tên_tiến_trình>`

*Ví dụ:*

    `pgrep firefox`

**Sử dụng pidof:**

    `pidof <tên_tiến_trình>`

*Ví dụ:*

    `pidof firefox`

**Sử dụng ps và grep:**

    `ps aux | grep <tên_tiến_trình>`

*Ví dụ:*

    `ps aux | grep firefox`

## Load average là gì?

- `Load average (trung bình tải)` là một chỉ số quan trọng trong hệ thống máy tính, đặc biệt là trên các hệ điều hành như Linux và Unix. 

- Nó thường được hiển thị dưới dạng ba con số, biểu thị tải trung bình trên hệ thống trong một khoảng thời gian cụ thể (thường là 1, 5 và 15 phút).

**Các con số trong load average thường được hiểu như sau:**

1. Load Average 1 phút: Chỉ số tải trung bình trong 1 phút gần đây nhất.

2. Load Average 5 phút: Chỉ số tải trung bình trong 5 phút gần đây nhất.

3. Load Average 15 phút: Chỉ số tải trung bình trong 15 phút gần đây nhất.

- Tác dụng chính của load average là cung cấp thông tin về mức độ bận rộn của hệ thống. Load average cao hơn cho thấy hệ thống đang gặp phải áp lực cao hơn từ các tiến trình đang chạy.

**Các tác dụng cụ thể của load average bao gồm:**

1. Đánh giá hiệu suất hệ thống: Load average là một chỉ số quan trọng để đánh giá hiệu suất của hệ thống. Nếu load average liên tục cao, điều này có thể chỉ ra rằng hệ thống đang bận rộn và có thể gặp phải vấn đề về hiệu suất.

2. Điều chỉnh tài nguyên: Dựa trên load average, người quản trị hệ thống có thể quyết định xem liệu hệ thống cần được mở rộng tài nguyên (ví dụ: thêm CPU, RAM) hay không.

3. Phát hiện vấn đề: Load average có thể giúp người quản trị hệ thống phát hiện các vấn đề sử lý hoặc tài nguyên sử dụng quá mức trên hệ thống.

>Tóm lại, `load average` là một công cụ quan trọng để đánh giá tình trạng hoạt động của hệ thống và có thể hỗ trợ trong việc quản lý và tối ưu hóa hiệu suất của hệ thống.

## Kiểm tra một phần mềm có đang chạy trên hệ thống không

**Để kiểm tra xem một phần mềm cụ thể có đang chạy trên hệ thống Linux hay không, bạn có thể sử dụng một số phương pháp sau:**

**Sử dụng lệnh pgrep:**

- Lệnh pgrep sẽ kiểm tra xem một tiến trình cụ thể có đang chạy hay không bằng cách tìm kiếm theo tên của tiến trình.

        pgrep <tên_tiến_trình>

    *Ví dụ:*
        
        pgrep firefox

- Nếu lệnh trả về một PID (Process ID), điều này có nghĩa là tiến trình đã được tìm thấy và đang chạy.

**Sử dụng lệnh ps và grep:**

- Lệnh `ps` cho phép bạn hiển thị danh sách các tiến trình đang chạy trên hệ thống. Bạn có thể kết hợp lệnh này với `grep` để tìm kiếm tiến trình cụ thể.

        ps aux | grep <tên_tiến_trình>

    *Ví dụ:*

        ps aux | grep firefox

- Nếu lệnh trả về kết quả, điều này có nghĩa là tiến trình đã được tìm thấy và đang chạy.

**Sử dụng htop:**

- Bạn có thể sử dụng htop để hiển thị danh sách các tiến trình đang chạy trên hệ thống một cách trực quan. Nếu phần mềm bạn đang kiểm tra đang chạy, bạn sẽ thấy nó trong danh sách.

        htop
    
- Nếu phần mềm đang chạy, bạn sẽ thấy nó trong danh sách và có thể kiểm tra các thông tin khác như CPU và RAM sử dụng của nó.






