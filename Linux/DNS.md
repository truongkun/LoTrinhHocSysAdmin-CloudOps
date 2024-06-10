# DNS

## DNS là gì?

- DNS là hệ thống phân giải tên miền từ tên miền sang ip và ngược lại.

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

- Recursive là truy vấn mà DNS Server sẽ phải đưa ra câu trả lời đầy đủ cho truy vấn đó hoặc đưa ra thông báo lỗi. Tức là với truy vấn này, DNS Server sẽ chịu trách nhiệm đi truy vấn hộ người dùng và lấy kết quả, sau đó trả lại kết quả cho người dùng.

- Interiative là truy vấn mà DNS Server có thể cung cấp câu trả lời hoặc 1 phần câu trả lời (như 1 lời giới thiệu) cho clients (hoặc đưa ra thông báo lỗi). Với truy vấn này, nếu DNS Server có câu trả lời cho truy vấn trong bộ nhớ đệm của nó, nó sẽ trả lại kết quả cho người dùng, nếu không, nó sẽ trả lại lời giới thiệu đến DNS Server biết được câu trả lời của truy vấn, để người dùng tự truy vấn.

- Non-recursive query: đã có kết quả truy vấn rồi, nên sẽ trả kq luôn, chứ k đi truy vấn như 2 thằng kia nữa
## Các bản ghi

- A Record: Bản ghi ánh xạ địa chỉ : còn được gọi là bản ghi máy chủ DNS, lưu trữ tên máy chủ và địa chỉ IPv4 tương ứng của nó.

- Bản ghi AAAA: Bản ghi địa chỉ IP Phiên bản 6 : lưu trữ tên máy chủ và địa chỉ IPv6 tương ứng của nó.

- Bản ghi CNAME: Bản ghi Tên chuẩn : chỉ định một tên miền phải được truy vấn để giải quyết truy vấn DNS gốc. Do đó, nó có thể được sử dụng để đặt tên máy chủ thành tên máy chủ khác.

- Bản ghi NS: Bản ghi Máy chủ tên : chỉ định rằng Vùng DNS, chẳng hạn như "example.com" được ủy quyền cho một Máy chủ tên có thẩm quyền cụ thể và cung cấp địa chỉ của máy chủ tên.

- Bản ghi SOA: Bắt đầu cấp phép : bản ghi này xuất hiện ở phần đầu của tệp vùng DNS và chỉ định thông tin cốt lõi về vùng DNS, chẳng hạn như Máy chủ tên có thẩm quyền cho vùng DNS hiện tại, chi tiết liên hệ của quản trị viên tên miền, số sê-ri tên miền và thông tin về tần suất thông tin DNS cho vùng này sẽ được làm mới.

- Bản ghi PTR: Ánh xạ ip thành tên miền