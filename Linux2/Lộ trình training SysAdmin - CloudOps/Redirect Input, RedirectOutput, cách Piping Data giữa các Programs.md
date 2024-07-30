# Redirect Input và Output, cách Piping Data giữa các Programs

## Redirect Input là gì

- `Redirect Input` là một kỹ thuật cho phép bạn chuyển hướng dữ liệu từ một nguồn khác vào đầu vào của một chương trình hoặc một lệnh.
- Cho phép bạn cung cấp dữ liệu từ một tệp tin hoặc từ một lệnh khác, thay vì nhập dữ liệu trực tiếp từ bàn phím.

**Ví dụ, để chạy một chương trình và cung cấp dữ liệu từ một tệp tin, bạn có thể sử dụng Redirect Input như sau:**

    command < input_file

Trong đó:

- command là tên của chương trình hoặc lệnh mà bạn muốn chạy.
- `<` là ký hiệu cho `Redirect Input`.
- `input_file` là tệp tin chứa dữ liệu bạn muốn chuyển hướng vào chương trình.

## Redirect Output là gì

- `Redirect Output` (chuyển hướng đầu ra) là một kỹ thuật cho phép bạn điều hướng đầu ra của một lệnh hoặc chương trình sang một vị trí cụ thể, thay vì hiển thị trực tiếp trên màn hình.
- Kỹ thuật này rất hữu ích khi bạn muốn **lưu trữ kết quả của một lệnh vào một tập tin** hoặc **sử dụng kết quả đó làm đầu vào cho một lệnh khác**.

**Có một số cách để redirect output trong Linux:**

1. Sử dụng ký hiệu >:

    ls > file_list.txt

Ví dụ: ls > file_list.txt **sẽ lưu danh sách các tệp tin trong thư mục hiện tại vào tập tin file_list.txt.**

2. Sử dụng ký hiệu >> để nối (append) đầu ra vào cuối tập tin:

    echo"Hello" >> greeting.txt

Ví dụ: echo "Hello" >> greeting.txt **sẽ thêm từ "Hello" vào cuối tập tin greeting.txt (nếu tập tin này đã tồn tại).**

3. Sử dụng ký hiệu 2> để redirect đầu ra lỗi (stderr):

    ls /nonexistent 2> error_log

Ví dụ: ls /nonexistent 2> error.log **sẽ ghi thông báo lỗi vào tập tin error.log thay vì hiển thị trên màn hình.**

4. Sử dụng ký hiệu &> để redirect cả đầu ra chuẩn và đầu ra lỗi:

    ls /nonexistent &> both.log

Ví dụ: ls /nonexistent &> both.log **sẽ ghi cả đầu ra chuẩn và đầu ra lỗi vào tập tin both.log.**

Redirect output datalà một công cụ mạnh mẽ trong Linux cho phép bạn điều hướng dữ liệu ra khỏi các lệnh và chương trình để lưu trữ hoặc xử lý dữ liệu một cách hiệu quả.

## Piping Data là gì

- "Piping data" trong Linux là một cách để **chuyển dữ liệu đầu ra của một chương trình thành đầu vào của một chương trình khác**.
- Cho phép bạn kết hợp các chương trình lại với nhau để thực hiện các nhiệm vụ phức tạp hơn mà không cần phải tạo ra các tập tin trung gian.

**Cú pháp chung cho việc piping data là sử dụng dấu gạch thẳng (|) để kết nối giữa các chương trình. Ví dụ:**

    command1 | command2

Trong đó:

- Command1 tạo ra đầu ra, và đầu ra đó được truyền vào
- Command2 như là đầu vào của nó

**Ví dụ cụ thể, để liệt kê tất cả các tệp tin trong thư mục hiện tại và sau đó sắp xếp chúng theo thứ tự từ A đến Z, bạn có thể sử dụng lệnh:**

    ls | sort

Ở đây, **ls tạo ra danh sách các tệp tin**, và **đầu ra của nó được truyền vào sort** để sắp xếp chúng.

**Một ví dụ khác là bạn muốn tìm kiếm các từ "error" trong một tập tin log và sau đó đếm số lượng lỗi. Bạn có thể sử dụng các lệnh grep và wc kết hợp với piping:**

    grep "error" logfile.txt | wc -l

Ở đây, **grep sẽ lọc ra tất cả các dòng có chứa từ "error" từ tập tin log** và **đưa chúng vào wc -l để đếm số lượng dòng**, cho bạn biết **số lượng lỗi trong tập tin.**

**Điều quan trọng** là khi sử dụng piping, đầu ra của chương trình đứng bên trước (command1) phải là dạng văn bản hoặc dữ liệu có thể được xử lý bởi chương trình kế tiếp (command2).
