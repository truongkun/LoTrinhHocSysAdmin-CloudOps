# DNS là gì?

- DNS, viết tắt của “Domain Name System”, là hệ thống quản lý và dịch tên miền (hostname) thành địa chỉ IP để truy cập các trang web trên internet. 

- Nó hoạt động dựa trên cấu trúc phân cấp và liên lạc với các máy chủ DNS để tìm kiếm thông tin về tên miền và địa chỉ IP tương ứng.

- Domain Name System có mục tiêu chính là đơn giản hóa việc truy cập và sử dụng internet bằng cách phân giải tên miền thành địa chỉ IP.

# Chức năng của Domain Name System

- Domain name system cũng giống như một cuốn danh bạ điện thoại. Nghĩa là thay vì phải nhớ hàng tá số điện thoại với một đống con số, thì bạn chỉ cần nhớ tên của chủ nhân số điện thoại thôi. Tương ứng với ví dụ này, số điện thoại sẽ là địa chỉ IP của Website, còn tên chủ nhân chính là tên miền của website đó.

> VD: khi bạn gõ “www.google.com” vào trình duyệt, máy chủ DNS sẽ lấy địa chỉ của máy chủ Google là “74.125.236.37”. Sau đó, bạn sẽ thấy trang home của Google tải trang trên trình duyệt mà bạn đang sử dụng. Đó là quá trình phân giải Domain Name System.


# Các loại máy chủ DNS sever 
- `Recursive server:` nhận các truy vấn DNS từ một ứng dụng, chẳng hạn như trình duyệt web.
  - khi resolver server nhận đc truy vấn nó sẽ kiểm tra bộ nhớ cache. Nếu ko thấy nó sẽ gửi truy vấn đến cấp độ cao hơn: DNS root server
>
- `DNS Root server:` Là dịch vụ phân giải tên miền gốc.
  - Tất cả tên miền trên thế giới đều phải thông qua DNS root server(như .com, .org, .vn, .net, ...)
  - Trên thế giới có 13 DNS root server: đc vận hành bởi 12 tổ chức khác nhau và mỗi root server có 1 địa chỉ ip duy nhất của riêng nó.
  >
  - Khi nhận đc truy vấn nó cũng không biết địa chỉ ip đó là gì, nhưng nó biết nơi nào cần hỏi để giúp reslver server tìm ra địa chỉ ip này. Trả hạn bạn tìm 1 tên miền có tên là .com thì root server sẽ điều hướng resolver đến top-level domain server của miền `.com`. Vì vậy resolver server sẽ gửi yêu cầu đến TLD server.
>
- `A top-level domain server:` Khi nhận đc truy vấn, tuy nó cx kb nhưng nó sẽ biết chính xác ai biết biết để lấy được thông tin này.
- top-level domain server sẽ điều hướng resolver server đến cấp độ tiếp theo là authoritative name server.
- Resolver server gửi truy vấn đến authoritative name server.
>
- `Authoritative name server:` là điểm kiểm tra cuối cùng cho truy vấn DNS. Những máy chủ này biết mọi thứ về một miền nhất định và xử lý phần miền phụ của tên miền. 
- Khi authoritative name server nhận đc truy vấn nó sẽ gửi địa chỉ ip tương ứng cho resolver server. Đồng thời resolver server sẽ lưu địa chỉ ip này vào trong cache để cho máy bạn hoặc người khác truy cập lần sau không phải thực hiện lại các bước trên nữa
- Cuối cùng resolver server sẽ cho máy tính bạn biết địa chỉ ip tương ứng.
- máy tính của bạn sẽ hiện thị thông tin cần yêu cầu.

# Các loại truy vấn DNS

Các loại truy vấn DNS sau đây là những loại truy vấn chính diễn ra ở các điểm khác nhau trong độ phân giải DNS:

- `Recursive DNS queries` là những `truy vấn` diễn ra giữa máy chủ đệ quy và máy khách. 
  - Câu trả lời được cung cấp là độ phân giải tên đầy đủ hoặc thông báo lỗi cho biết không thể tìm thấy tên. Truy vấn đệ quy kết thúc bằng câu trả lời hoặc lỗi.
>
- `Iterative DNS queries` diễn ra giữa trình phân giải đệ quy, là máy chủ DNS cục bộ và các máy chủ tên không cục bộ, như máy chủ gốc, TLD và máy chủ tên có thẩm quyền. Các truy vấn lặp lại không yêu cầu phân giải tên; thay vào đó, các máy chủ định danh có thể phản hồi bằng một giới thiệu. Máy chủ gốc giới thiệu máy chủ đệ quy đến TLD, tham chiếu nó đến máy chủ có thẩm quyền. Máy chủ có thẩm quyền cung cấp tên miền cho máy chủ đệ quy nếu có. Các truy vấn lặp lại giải quyết bằng câu trả lời hoặc giới thiệu.
>
- `Nonrecursive queries` là những truy vấn mà trình phân giải đệ quy đã biết nơi nhận câu trả lời. Câu trả lời được lưu vào bộ nhớ đệm trên máy chủ đệ quy hoặc máy chủ đệ quy biết bỏ qua máy chủ gốc và máy chủ TLD và truy cập trực tiếp vào một máy chủ có thẩm quyền cụ thể. Nó không đệ quy vì không cần -- và do đó, không có yêu cầu -- đối với bất kỳ truy vấn nào nữa. Các truy vấn không đệ quy giải quyết trong câu trả lời. Nếu trình phân giải đệ quy đã lưu trữ địa chỉ IP từ phiên trước đó và phục vụ địa chỉ đó theo yêu cầu tiếp theo thì đó được coi là truy vấn không đệ quy.

# Các loại DNS bản ghi DNS phổ biến

Có nhiều loại bản ghi DNS, mỗi loại có mục đích riêng trong việc biểu thị cách xử lý một truy vấn. Các bản ghi DNS phổ biến như sau:

- `A record:` Đây là viết tắt của địa chỉ và giữ địa chỉ IP của một tên miền. Bản ghi chỉ áp dụng cho địa chỉ IPv4. Thay vào đó, địa chỉ IPv6 có bản ghi AAAA, sử dụng định dạng dài hơn của địa chỉ IPv6. Hầu hết các trang web chỉ có một bản ghi A, nhưng một số trang web lớn hơn có nhiều bản ghi, giúp cân bằng tải bằng cách cung cấp các bản ghi A khác nhau cho những người dùng khác nhau khi có lưu lượng truy cập lớn.
>
- `NS record:` Các bản ghi máy chủ tên này biểu thị máy chủ có thẩm quyền nào chịu trách nhiệm có tất cả thông tin về một tên miền nhất định. Thông thường, các miền có cả máy chủ định danh chính và dự phòng để tăng độ tin cậy và nhiều bản ghi NS được sử dụng để truy vấn trực tiếp tới chúng.
>
- `TXT record:` Bản ghi TXT cho phép quản trị viên nhập văn bản vào DNS. Mục đích ban đầu là đưa các ghi chú mà con người có thể đọc được vào DNS, nhưng ngày nay, các ghi chú mà máy có thể đọc được thường được đặt ở đó.  
  - TXT record: được sử dụng để xác nhận quyền sở hữu tên miền, bảo mật email và chống thư rác.
>
- `CNAME record:` Bản ghi tên chuẩn được sử dụng thay cho bản ghi A khi có bí danh. Chúng được sử dụng để thử lại truy vấn của cùng một địa chỉ IP với hai miền khác nhau. Một ví dụ là trong URL searchsecurity.techtarget.com, trong đó CNAME sẽ truy vấn techtarget.com.
