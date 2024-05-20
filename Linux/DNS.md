# DNS

## DNS là gì?

- DNS là hệ thống phân giải tên miền. 
- DNS là hệ thống cho phép thiết lập tương ứng giữa địa chỉ ip và tên miền trên internet.

## DNS dùng để  làm gì?

- DNS dùng để dịch các tên miền dễ nhớ của con người (như www.example.com) thành các địa chỉ IP mà máy tính sử dụng để định vị và giao tiếp với nhau trên mạng (như 192.0.2.1).

## Các loại DNS server?

**DNS Recursor** là máy chủ chịu trách nhiệm truy vấn đệ quy. Được hoạt động như 1 thư viện, lưu trữ thông tin về địa chỉ IP của trang web và ứng dụng. 
- Khi người dùng nhập 1 tên miền, DNS recursor sẽ tìm kiếm thông tin đó trong bộ nhớ cache của mình.

**Root nameserver** là dịch vụ phân giải tên miền gốc và trên thế giới có khoảng 13 DNS root server.

- `Root nameserver :` chứa toàn bộ các thông tin về domain và IP của các Top Level Domain (TLD) Nameserver. 

- Khi có truy vấn được gửi đến nó, root nameserver sẽ trả lại thông tin của TLD Nameserver để client tiếp tục truy vấn kết quả

**Top-level-domain nameserver**  

- Là nameserver chứa toàn bộ thông tin về mọi tên miền cùng chung phần mở rộng tên miền như .com, .vn, .net,…  

- Khi nhận được truy vấn, TLD nameserver sẽ trả lại cho client thông tin của Authoritative Nameserver quản lý tên miền đang được truy vấn.

**Autheratitive** Authoritative Name Server lưu trữ thông tin về tên miền và địa chỉ IP tương ứng. Là điểm cuối của quá trình truy vấn và phân giải địa chỉ IP cần thiết cho DNS Recursor.

## Quá trình hoạt động DNS server

Quá trình phân giải tên miền (DNS resolution) cho tên miền facebook.com bao gồm các bước sau đây:

### 1. Trình duyệt kiểm tra bộ nhớ đệm cục bộ (Local Cache)
Trước khi gửi yêu cầu ra mạng, trình duyệt sẽ kiểm tra bộ nhớ đệm (cache) của chính nó để xem liệu tên miền facebook.com đã được phân giải gần đây và lưu trữ trong bộ nhớ đệm hay không. Nếu tìm thấy, quá trình phân giải tên miền kết thúc tại đây.

### 2. Hệ điều hành kiểm tra bộ nhớ đệm cục bộ
Nếu trình duyệt không tìm thấy tên miền trong bộ nhớ đệm của nó, nó sẽ yêu cầu hệ điều hành (OS) kiểm tra bộ nhớ đệm DNS của hệ điều hành. Nếu hệ điều hành có bản ghi DNS tương ứng trong bộ nhớ đệm của nó, quá trình phân giải tên miền kết thúc tại đây.

### 3. Trình phân giải DNS (DNS Resolver) của nhà cung cấp dịch vụ Internet (ISP)
Nếu hệ điều hành không có bản ghi DNS trong bộ nhớ đệm, nó sẽ gửi yêu cầu đến trình phân giải DNS của nhà cung cấp dịch vụ Internet (ISP). Trình phân giải DNS này sẽ kiểm tra bộ nhớ đệm của nó trước khi thực hiện các bước tiếp theo.

### 4. Truy vấn tới máy chủ gốc (Root Server)
Nếu trình phân giải DNS của ISP không tìm thấy bản ghi trong bộ nhớ đệm của nó, nó sẽ gửi truy vấn đến một trong các máy chủ gốc (Root Server). Máy chủ gốc sẽ không cung cấp câu trả lời cuối cùng nhưng sẽ hướng dẫn trình phân giải DNS tới máy chủ DNS cấp cao hơn (Top-Level Domain, TLD).

### 5. Truy vấn tới máy chủ TLD
Máy chủ gốc sẽ trả về địa chỉ của máy chủ TLD quản lý tên miền cấp cao nhất của facebook.com, cụ thể là máy chủ TLD .com. Trình phân giải DNS của ISP sẽ tiếp tục gửi truy vấn đến máy chủ TLD .com.

### 6. Truy vấn tới máy chủ DNS thẩm quyền (Authoritative DNS Server)
Máy chủ TLD sẽ trả về địa chỉ của máy chủ DNS thẩm quyền cho tên miền facebook.com. Trình phân giải DNS của ISP sẽ gửi truy vấn đến máy chủ DNS thẩm quyền này.

### 7. Nhận phản hồi từ máy chủ DNS thẩm quyền
Máy chủ DNS thẩm quyền cho tên miền facebook.com sẽ trả về địa chỉ IP tương ứng với tên miền facebook.com. Đây là kết quả cuối cùng của quá trình phân giải tên miền.

### 8. Trả kết quả về cho trình duyệt
Trình phân giải DNS của ISP sẽ gửi địa chỉ IP này về cho hệ điều hành, hệ điều hành sẽ gửi lại cho trình duyệt. Trình duyệt nhận được địa chỉ IP và tiến hành kết nối tới máy chủ web của facebook.com bằng địa chỉ IP này.

### Tổng kết quá trình:
1. Trình duyệt kiểm tra bộ nhớ đệm.
2. Hệ điều hành kiểm tra bộ nhớ đệm.
3. Trình phân giải DNS của ISP kiểm tra bộ nhớ đệm.
4. Truy vấn tới máy chủ gốc.
5. Truy vấn tới máy chủ TLD .com.
6. Truy vấn tới máy chủ DNS thẩm quyền cho facebook.com.
7. Nhận địa chỉ IP từ máy chủ DNS thẩm quyền.
8. Trả kết quả về cho trình duyệt.

Thông qua quá trình này, tên miền facebook.com được phân giải thành địa chỉ IP, cho phép trình duyệt kết nối và hiển thị trang web.

## 3 loại truy vấn DNS

- Recursive query: DNS client yêu cầu máy chủ DNS (thường là recursive DNS resolver). Sẽ trả lời máy khách bằng bản ghi tài nguyên được yêu cầu. Hoặc thông báo lỗi nếu resolver không thể tìm thấy bản ghi.
- Iterative query: Trong tình huống này, DNS client sẽ cho phép máy chủ DNS trả về câu trả lời tốt nhất có thể. Nếu máy chủ DNS được truy vấn không có kết quả trùng khớp với tên truy vấn. Nó sẽ trả về một giới thiệu đến máy chủ DNS có thẩm quyền cho mức thấp hơn. DNS client sau đó sẽ thực hiện một truy vấn đến địa chỉ được giới thiệu. Quá trình này tiếp tục với các máy chủ DNS bổ sung trong chuỗi truy vấn cho đến khi xảy ra lỗi hoặc hết thời gian.
- Non-recursive query: Thông thường điều này sẽ xảy ra khi DNS resolver client truy vấn máy chủ DNS một record mà server có quyền truy cập hoặc bản ghi tồn tại bên trong bộ đệm của server. Thông thường, một máy chủ DNS sẽ lưu các bản ghi DNS để ngăn chặn việc tiêu thụ thêm băng thông và giảm tải cho các máy chủ DNS khác.