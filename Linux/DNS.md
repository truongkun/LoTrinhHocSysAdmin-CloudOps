# DNS là gì?

- DNS, viết tắt của “Domain Name System”, là hệ thống quản lý và dịch tên miền (hostname) thành địa chỉ IP để truy cập các trang web trên internet. 
>
## Chức năng của Domain Name System

- Domain name system cũng giống như một cuốn danh bạ điện thoại. Nghĩa là thay vì phải nhớ hàng tá số điện thoại với một đống con số, thì bạn chỉ cần nhớ tên của chủ nhân số điện thoại thôi. Tương ứng với ví dụ này, số điện thoại sẽ là địa chỉ IP của Website, còn tên chủ nhân chính là tên miền của website đó.

## Cơ chế hoạt động của DNS

Cơ chế hoạt động của DNS (Domain Name System) được thực hiện 1 truy vấn như sau:

1. **Recursor Nameserver**: (trung gian)
   - Khi một máy tính hoặc thiết bị kết nối với internet cần phải truy vấn một địa chỉ IP cho một tên miền như "example.com", nó sẽ gửi yêu cầu này đến Recursor Nameserver.
   - Recursor Nameserver sẽ kiểm tra trong bộ nhớ cache của nó xem nó đã lưu trữ thông tin cho tên miền này trước đó hay không. Nếu có, nó sẽ trả về địa chỉ IP từ cache.
   - Nếu thông tin không được tìm thấy trong cache, Recursor Nameserver sẽ bắt đầu quá trình tìm kiếm bằng cách gửi yêu cầu truy vấn đến các máy chủ DNS khác để tìm ra địa chỉ IP phù hợp.

2. **Root NameServer**:
   - Nếu Recursor Nameserver không tìm thấy thông tin trong cache của mình, nó sẽ gửi yêu cầu truy vấn đến một trong 13 máy chủ Root NameServer trên toàn cầu.
   - Root NameServer sẽ trả lời với thông tin về TLD (Top-Level-Domain) NameServer phù hợp dựa trên phần mở rộng của tên miền được truy vấn. 
   - Ví dụ, nếu tên miền là "example.com", Root NameServer sẽ trả lại thông tin về máy chủ TLD cho miền ".com".

3. **Top-Level-Domain NameServer**:
   - Recursor Nameserver sau đó gửi yêu cầu truy vấn tiếp theo đến máy chủ TLD NameServer cho phần mở rộng của tên miền (ví dụ: .com).
   - TLD NameServer sẽ trả lại thông tin về máy chủ Authoritative NameServer cho tên miền được truy vấn, chẳng hạn như "example.com".

4. **Authoritative NameServer**:
   - Cuối cùng, Recursor Nameserver gửi yêu cầu truy vấn cuối cùng đến máy chủ Authoritative NameServer cho tên miền cụ thể.
   - Authoritative NameServer sẽ trả về địa chỉ IP chính xác của tên miền "example.com".
   - Recursor Nameserver lưu trữ thông tin này trong bộ nhớ cache của mình để sử dụng cho các truy vấn tương lai và cung cấp địa chỉ IP cho client gửi yêu cầu ban đầu.

## Các loại máy chủ DNS server   

- `Recursor Nameserver` là một máy chủ có nhiệm vụ chuyển đổi tên miền thành địa chỉ IP. Được hoạt động như một thư viện, lưu trữ thông tin về địa chỉ IP của các trang web và ứng dụng. 
    
- `Root NameServer:` là dịch vụ phân giải tên miền gốc. Trên thế giới có tất cả 12 DNS root Server. 
  - `DNS root Server` quản lý tất cả các tên miền Top-level. Nó chứa tất cả thông tin về domain và ip của các Top-level-domain nameserver.
    ![alt text](/Linux/img/dns-root-server.png)
  - `VD:` Khi truy vấn đến Root NameServer, Root Nameserver sẽ trả lại thông tin TLD Nameserver để client tiếp tục truy vấn kết quả.
- `Top-Level-Domain NameServer:` là máy chủ tên miền cấp cao nhất, chịu trách nhiệm lưu trữ thông tin về các tên miền có phần mở rộng chung (gTLD), chẳng hạn như .com, .org, .net.
    - VD: Khi nhận đc truy vấn, TLD Nameserver sẽ trả lại cho client thông tin Authoritative Nameserver nơi quản lý tên miền đang được truy vấn 
- `Authoritative NameServer:` là nơi lưu trữ thông tin về tên miền và địa chỉ IP mà nó quản lý. Là điểm cuối của quá trình truy vấn và phân giải địa chỉ IP cần thiết cho Recursor Nameserver.

![alt text](img/dns2.png)

## Các loại truy vấn DNS
- `Truy vấn Recursive:` DNS client yêu cầu máy chủ DNS trả về kết quả hoặc thông báo lỗi nếu không tìm thấy bản ghi tài nguyên.
>
- `Truy vấn Iterative:` Nếu DNS Server không có địa chỉ IP, nó sẽ trả về Authoritative Name Server hoặc TLD Name Server và quá trình này sẽ lặp đi lặp lại cho đến khi có kết quả hoặc đạt đến giới hạn thời gian.
>
- `Truy vấn Non-Recursive:` DNS client yêu cầu máy chủ DNS cho một bản ghi cụ thể mà máy chủ đã lưu trữ trong bộ nhớ cache của mình, giúp giảm tải cho hệ thống DNS bằng cách tránh việc truy cập lại Internet để lấy thông tin.
### Các loại Query trong DNS

- **Recursive query**: DNS client yêu cầu máy chủ DNS (thường là Recursor nameserver). Sẽ trả lời máy khách bằng bản ghi tài nguyên được yêu cầu. Hoặc thông báo lỗi nếu resolver không thể tìm thấy bản ghi.

- **Iterative query**: Là truy vấn mà DNS Server có thể cung cấp câu trả lời hoặc 1 phần câu trả lời (như 1 lời giới thiệu) cho clients (hoặc đưa ra thông báo lỗi). Với truy vấn này, nếu DNS Server có câu trả lời cho truy vấn trong bộ nhớ đệm của nó, nó sẽ trả lại kết quả cho người dùng, nếu không, nó sẽ trả lại lời giới thiệu đến DNS Server biết được câu trả lời của truy vấn, để người dùng tự truy vấn.

- **Non-recursive query**: Thông thường điều này sẽ xảy ra khi DNS resolver client truy vấn máy chủ DNS một record mà server có quyền truy cập hoặc bản ghi tồn tại bên trong bộ đệm của server. Thông thường, một máy chủ DNS sẽ lưu các bản ghi DNS để ngăn chặn việc tiêu thụ thêm băng thông và giảm tải cho các máy chủ DNS khác.

### Các DNS Record thường dùng

- **A record** : dùng để phân giải tên miền địa chỉ ipv4.

- **AAAA record** : dùng để phân giải tên miền địa chỉ ipv6.

- **CNAME record** : dùng để phân giải tên miền phụ thành tên miền đích

- **NS record** : Có chức năng chỉ ra địa chỉ DNS server

- **MX record** : có chức năng chỉ ra địa chỉ mail server. MX Record chỉ định server nào quản lý các dịch vụ Email của tên miền đó.

- **PTR Record** : dùng để phân giải địa chỉ ip sang tên miền.

- **SRV record** : dùng để xác định vị trí của các dịch vụ đặc biệt trong đường mạng 

- **TXT Record** : chứa các dữ liệu theo định dạng văn bản thường dùng để xác thực nguời sử dụng tên miền.