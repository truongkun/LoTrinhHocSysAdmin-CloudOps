# 1. Giới thiệu về DNS

____

# Mục lục


- [1. Giới thiệu về DNS](#1-giới-thiệu-về-dns)
- [Mục lục](#mục-lục)
- [Nội dung](#nội-dung)
    - [1.1 DNS là gì?](#11-dns-là-gì)
    - [1.2 Vai trò, chức năng của DNS](#12-vai-trò-chức-năng-của-dns)
    - [1.3 Cách thức hoạt động của DNS](#13-cách-thức-hoạt-động-của-dns)
    - [1.4 Các loại máy DNS ](#14-các-loại-máy-dns-)
      - [1.4.1.Recursive DNS Server (DNS Máy chủ Đệ Quy):](#141recursive-dns-server-dns-máy-chủ-đệ-quy)
      - [1.4.2. Authoritative DNS Server (DNS Máy chủ Chính Thức):](#142-authoritative-dns-server-dns-máy-chủ-chính-thức)
      - [1.4.3. Caching DNS Server (DNS Máy chủ Lưu Trữ Tạm Thời):](#143-caching-dns-server-dns-máy-chủ-lưu-trữ-tạm-thời)
    - [Các loại truy vấn DNS là gì?](#các-loại-truy-vấn-dns-là-gì)
      - [3 loại truy vấn DNS:](#3-loại-truy-vấn-dns)
    - [1.5 cách tìm ip của domain dantri.vn bằng command trong linux ](#15-cách-tìm-ip-của-domain-dantrivn-bằng-command-trong-linux-)
      - [Sử dụng lệnh `dig`:](#sử-dụng-lệnh-dig)
      - [Sử dụng lệnh `nslookup`:](#sử-dụng-lệnh-nslookup)

____

# <a name="content">Nội dung</a>

### <a name="what-is">1.1 DNS là gì?</a>

- `DNS` viết tắt của `Domain Name System` có nghĩa là hệ thống phân giải tên miền. DNS là hệ thống cho phép thiết lập tương ứng giữa địa chỉ IP và tên miền trên Internet.

    ![dns-root.png](img/dns-la-gi.jpg)

- Thế nào là DNS?

    ![alt text](img/image.png)

### <a name="whyfeature">1.2 Vai trò, chức năng của DNS</a>

- DNS đóng vai trò `như một “biên dịch viên” giữa tên miền và địa chỉ IP`. Tên miền là chuỗi ký tự dễ nhớ, trong khi địa chỉ IP là chuỗi số khó nhớ. DNS `giúp chuyển đổi tên miền thành địa chỉ IP`, từ đó giúp máy tính có thể truy cập vào các trang web trên internet.

- Mỗi máy tính khi kết nối vào Internet sẽ được gán cho 1 địa chỉ IP (Ví dụ: 1414.1158.62462) riêng biệt và không trùng lẫn với bất kỳ máy tính nào khác trên thế giới. Cũng giống như vậy đối với website cũng có địa chỉ IP riêng biệt của website đó.

    ![alt text](img/image1.png)

- Tuy nhiên, mỗi website đề có một địa chỉ IP là các con số khá dài và khó nhớ khiến bạn không thể nhớ rõ con số IP đó.

**Ví dụ:**
```
Địa chỉ IP là 103.200.21.192 dẫn đến website Vietnix thay vì gõ vietnix.vn trên thanh tìm kiếm. 
Lúc này là lúc DNS “trổ tài chuyển đổi” (ánh xạ) dãy số địa chỉ IP thành những ký tự thân thiện hơn. 
Chính vì nhờ có giao thức DNS nên bạn không cần phải nhớ địa chỉ IP để vào website Vietnix mà chỉ cần nhớ vietnix.vn là được.
```

- Nói cách khác, `DNS` cũng giống như một danh bạ điện thoại dành riêng cho Internet. Nếu bạn biết tên của một người nhưng không biết số điện thoại hay ngược lại, bạn có thể tham khảo trong sổ danh bạ dễ dàng.

### <a name="How it works">1.3 Cách thức hoạt động của DNS</a>

- Khi người dùng truy cập một website, máy tính sẽ gửi yêu cầu đến máy chủ DNS cục bộ để tìm địa chỉ IP của website đó. Máy chủ DNS cục bộ sẽ kiểm tra cơ sở dữ liệu của mình xem có chứa địa chỉ IP của website hay không. Nếu có, sẽ trả về địa chỉ IP cho máy tính của người dùng.
- Quá trình phân giải DNS bao gồm chuyển đổi tên máy chủ (chẳng hạn như www.example.com) thành địa chỉ IP thân thiện với máy tính (chẳng hạn như 192.168.1.1). Một địa chỉ IP được cung cấp cho mỗi thiết bị trên Internet và địa chỉ đó là cần thiết để tìm thiết bị. Internet phù hợp. Giống như một địa chỉ đường phố được sử dụng để tìm một ngôi nhà cụ thể.
- Khi người dùng muốn tải một trang web, một bản dịch phải xảy ra giữa những gì người dùng nhập vào trình duyệt web của họ (example.com) và địa chỉ thân thiện với máy cần thiết để định vị trang web example.com.
- Nếu máy chủ DNS cục bộ không có địa chỉ IP của website, nó sẽ hỏi máy chủ DNS gốc. Máy chủ DNS gốc sẽ trả về địa chỉ IP của máy chủ DNS cấp cao nhất cho website.
- Máy chủ DNS cấp cao nhất sẽ trả về địa chỉ IP của máy chủ DNS quản lý website. Máy chủ DNS quản lý sẽ trả về địa chỉ IP của trang web cho máy chủ DNS cục bộ.
- Cuối cùng, máy chủ DNS cục bộ sẽ trả về địa chỉ IP của trang web cho máy tính của người dùng. Máy tính của người dùng sẽ sử dụng địa chỉ IP này để kết nối với website.

### <a name="Các máy chủ DNS">1.4 Các loại máy DNS </a>

- Việc chọn máy chủ DNS phù hợp và tốt nhất phụ thuộc vào nhiều yếu tố, bao gồm tốc độ, độ tin cậy và sự phù hợp với khu vực địa lý của người dùng. Dưới đây là một số gợi ý về những máy chủ DNS tốt nhất hiện nay:

#### 1.4.1.Recursive DNS Server (DNS Máy chủ Đệ Quy):

- Đây là loại máy chủ DNS mà các máy tính và thiết bị trong mạng thông thường kết nối đến để thực hiện các truy vấn DNS.
- DNS máy chủ đệ quy sẽ tìm kiếm thông tin DNS từ Internet và trả về cho người dùng hoặc thiết bị yêu cầu.
- Ví dụ: Google DNS, OpenDNS.

#### 1.4.2. Authoritative DNS Server (DNS Máy chủ Chính Thức):

- Đây là loại máy chủ DNS chứa thông tin chính xác về một tên miền cụ thể, bao gồm các bản ghi DNS như A, AAAA, MX, CNAME, v.v.
- Các máy chủ DNS chính thức cung cấp thông tin cho các truy vấn DNS liên quan đến tên miền mà chúng được cấu hình để quản lý.
- Ví dụ: Máy chủ DNS của tên miền, như máy chủ DNS của Google cho tên miền google.com.

#### 1.4.3. Caching DNS Server (DNS Máy chủ Lưu Trữ Tạm Thời):

- Đây là loại máy chủ DNS lưu trữ thông tin từ các truy vấn trước đó trong một kho dữ liệu tạm thời.
- Khi một truy vấn DNS được thực hiện, máy chủ lưu trữ tạm thời có thể trả về kết quả từ bộ nhớ cache thay vì phải truy vấn lại từ Internet.
- Điều này giúp cải thiện hiệu suất và giảm tải cho máy chủ DNS chính thức và Internet nói chung.

Mỗi loại máy chủ DNS phục vụ một mục đích cụ thể và đóng vai trò quan trọng trong việc đảm bảo hoạt động hiệu quả và đáng tin cậy của cơ sở hạ tầng Internet.

### Các loại truy vấn DNS là gì?

Trong quá trình tra cứu DNS thông thường, có ba loại truy vấn xảy ra. Bằng cách sử dụng kết hợp các truy vấn này, quy trình được tối ưu hóa cho độ phân giải DNS có thể giúp giảm khoảng cách di chuyển. Trong tình huống lý tưởng, dữ liệu bản ghi được lưu trong bộ nhớ cache sẽ có sẵn, cho phép máy chủ tên DNS trả về truy vấn không đệ quy.

#### 3 loại truy vấn DNS:

1. `Recursive query(Truy vấn đệ quy)` - Trong truy vấn đệ quy, máy khách DNS yêu cầu máy chủ DNS (thường là trình phân giải đệ quy DNS) sẽ phản hồi máy khách bằng bản ghi tài nguyên được yêu cầu hoặc thông báo lỗi nếu trình phân giải không thể tìm thấy bản ghi.
2. `Iterative query(Truy vấn lặp lại)` - trong trường hợp này, máy khách DNS sẽ cho phép máy chủ DNS trả về câu trả lời tốt nhất có thể. Nếu máy chủ DNS được truy vấn không khớp với tên truy vấn, nó sẽ trả về một tham chiếu đến máy chủ DNS có thẩm quyền ở cấp độ thấp hơn của không gian tên miền. Sau đó, máy khách DNS sẽ thực hiện truy vấn đến địa chỉ được giới thiệu. Quá trình này tiếp tục với các máy chủ DNS bổ sung trong chuỗi truy vấn cho đến khi xảy ra lỗi hoặc hết thời gian chờ.
3. `Non-recursive query(Truy vấn không đệ quy)` - thông thường, điều này sẽ xảy ra khi máy khách trình phân giải DNS truy vấn máy chủ DNS để tìm bản ghi mà nó có quyền truy cập vì nó có thẩm quyền đối với bản ghi hoặc bản ghi tồn tại bên trong bộ đệm của nó. Thông thường, máy chủ DNS sẽ lưu vào bộ đệm các bản ghi DNS để ngăn chặn việc tiêu thụ và tải thêm băng thông trên các máy chủ ngược dòng.


### <a>1.5 cách tìm ip của domain dantri.vn bằng command trong linux </a>

-Bạn có thể sử dụng lệnh `dig` hoặc `nslookup` để tìm địa chỉ IP của tên miền "dantri.vn" trong Linux. Dưới đây là cách thực hiện bằng cả hai lệnh:

#### Sử dụng lệnh `dig`:

```
dig +short dantri.vn
```

#### Sử dụng lệnh `nslookup`:

```
nslookup dantri.vn
```

Kết quả sẽ hiển thị một hoặc nhiều địa chỉ IP liên quan đến tên miền "dantri.vn". Địa chỉ IP được liệt kê thường là các máy chủ web hoặc máy chủ DNS của tên miền đó.


