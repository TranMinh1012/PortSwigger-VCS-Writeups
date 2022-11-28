# Directory Traversal
## Reading arbitrary files via directory traversal
**Lab1: File path traversal, simple case**

Bước 1: Truy cập vào một sản phẩm bất kỳ và bắt request đấy

Bước 2: Forward đến khi thấy được đường dẫn lấy ảnh của sản phẩm

![image](https://user-images.githubusercontent.com/74781135/203206978-90662905-73d5-48b8-9bb6-98cafa182b74.png)

Bước 3: Gửi request này đến repeater và sửa đổi đường dẫn thành **/image?filename=../../../etc/passwd**. 

"../" hợp lệ trong một đường dẫn tệp và có nghĩa là tăng một bậc trong cấu trúc thư mục. Ba chuỗi "../" liên tiếp tăng dần từ /var/www/images đến thư mục root của hệ thống tệp => tệp thực sự được đọc ra là: **/etc/passwd**

Gửi request thì phản hồi sẽ thu được danh sách mật khẩu

![image](https://user-images.githubusercontent.com/74781135/203207160-d77230a7-1da0-4499-aece-d4945caf0dd5.png)

## Common obstacles to exploiting file path traversal vulnerabilities
**Lab2: File path traversal, traversal sequences blocked with absolute path bypass**

Bước 1: Truy cập vào một sản phẩm bất kỳ vào bắt request

Bước 2: Forward đến khi thấy được đường dẫn lấy ảnh của sản phấm

![image](https://user-images.githubusercontent.com/74781135/203208697-54e747ed-40b8-44f9-af3e-06d34d1b5aa6.png)

Có thể sử dụng một đường dẫn tuyệt đối từ thư mục gốc của hệ thống tập tin để tham chiếu trực tiếp một tệp mà không sử dụng bất kỳ trình tự truyền tải nào.

Bước 3: Gửi request này đến repeater và sửa đổi đường dẫn thành **/image?filename=/etc/passwd**. Gửi request thì phản hồi sẽ thu được danh sách mật khẩu

![image](https://user-images.githubusercontent.com/74781135/203208854-232c527b-c42c-49ad-a669-d0225b99770a.png)

**Lab3: File path traversal, traversal sequences stripped non-recursively**

Bước 1: Truy cập vào một sản phẩm bất kỳ và bắt request đấy

Bước 2: Forward đến khi thấy được đường dẫn lấy ảnh của sản phẩm

![image](https://user-images.githubusercontent.com/74781135/203211934-f8398fd4-3ca2-4e02-946c-77194b29415a.png)

Nếu sequences (../) bị loại khỏi đầu vào của người dùng thì nó chỉ xóa tất cả các lần xuất hiện của ../ khỏi tên tệp. Dó đó, đầu vào của ../../../etc/passwd sẽ trở thành đường dẫn tương đối etc/passwd không tồn tại. 

Nhưng nếu chỉ xóa các chuỗi "../", chỉ cần cung cấp một chuỗi đại diện cho chuỗi duyệt đường dẫn sau khi xóa. Do đó "....//" sẽ trở thành "../" (Hai dấu chấm đầu tiên và dấu gạch chéo cuối cùng vẫn còn sau khi xóa)

Bước 3: Gửi request này đến repeater và sửa đổi đường dẫn thành **/image?filename=....//....//....//etc/passwd**. Gửi request thì phản hồi sẽ thu được danh sách mật khẩu

![image](https://user-images.githubusercontent.com/74781135/203212108-303c7d11-b7a8-48ec-b7dc-88ecd9c161ec.png)

**Lab4: File path traversal, traversal sequences stripped with superfluous URL-decode**

Bước 1: Truy cập vào một sản phẩm bất kỳ và bắt request đấy

Bước 2: Forward đến khi thấy được đường dẫn lấy ảnh của sản phẩm

![image](https://user-images.githubusercontent.com/74781135/203213180-b9ed5e04-d406-4c6b-a5c2-4c446f9ecb1e.png)

Theo như mô tả của bài lab, thì ứng dụng sẽ xóa các trình tự truyền tải đường dẫn trước sau đó giải mã URL đầu vào. Để lấy được danh sách mật khẩu thì cần mã hóa "../"

Trong trường hợp các ký tự nằm trong phạm vi ASCII thông thường, ký tự đó được biểu thị bằng %, theo sau là giá trị ASCII của nó ở dạng hex.

![image](https://user-images.githubusercontent.com/74781135/203570224-c726ce32-af40-4164-91d1-eb4cd27eec88.png)

Máy chủ thường thực hiển 1 cấp độ giải mã URL khi nhận được yêu cầu nên mã hóa "../" thành "%2e%2e%2f" là không đủ. Để vượt qua cấp độ này cần mã hóa cả ký tự "%"

`. --> %2e`

`/ --> %2f`

`% --> %25`

Do đó "../" sẽ mã hóa thành "%252e%252e%252f".

Bước 3: Gửi request này đến repeater và sửa đổi đường dẫn thành **/image?filename=%252e%252e%252f%252e%252e%252f%252e%252e%252f/etc/passwd**. Gửi request thì phản hồi sẽ thu được danh sách mật khẩu

![image](https://user-images.githubusercontent.com/74781135/203213610-1e4e446a-592b-4256-a187-380e420b24e5.png)

**Lab5: File path traversal, validation of start of path**

Bước 1: Truy cập vào một sản phẩm bất kỳ và bắt request đấy

Bước 2: Forward đến khi thấy được đường dẫn lấy ảnh của sản phẩm

![image](https://user-images.githubusercontent.com/74781135/203214348-1343bd52-86a4-48d7-8e4c-504a68f3cadb.png)

Ứng dụng kiểm tra xem đường dẫn có bắt đầu với các giá trị dự kiến hay không, trong trường hợp này là đường dẫn tuyệt đối **/var/www/images**. Vì vậy không thể có các đường dẫn tuyệt đối khác (/etc/passwd) cũng như các đường dẫn tương đối (../../../etc/passwd).

=> Có thể tham chiếu bất kỳ tệp nào trên hệ thống miễn là đường dẫn đó là tuyệt đối và bắt đầu bằng /var/www/images/.

Bước 3: Gửi request này đến repeater và sửa đổi đường dẫn thành **/image?filename=/var/www/images/../../../etc/passwd**. Gửi request thì phản hồi sẽ thu được danh sách mật khẩu

![image](https://user-images.githubusercontent.com/74781135/203214576-034e5cb6-7960-4e91-8399-3957aaedb8ae.png)

**Lab6: File path traversal, validation of file extension with null byte bypass**

Bước 1: Truy cập vào một sản phẩm bất kỳ và bắt request đấy

Bước 2: Forward đến khi thấy được đường dẫn lấy ảnh của sản phẩm

![image](https://user-images.githubusercontent.com/74781135/203215162-211250d4-5a29-42a0-8815-afc2f4958fbe.png)

Bước 3: Gửi request này đến Repeater và thử sửa đường dẫn thành /image?filename=../images/72.jpg

![image](https://user-images.githubusercontent.com/74781135/203581972-293df9cc-a676-4be1-bf84-fb9ab303fc6e.png)

Có thể thấy ta thu được ảnh

Bước 4: Thử với đường dẫn /image?filename=../images/72.png

![image](https://user-images.githubusercontent.com/74781135/203582290-f2df5d9f-7d89-4f22-8a8b-42fb28cf9a1e.png)

Ta không thu được ảnh =>  phần mở rộng tệp đã được kiểm tra

Rất nhiều phần mềm cấp thấp như hệ điều hành được viết bằng C. Trong ngôn ngữ đó, các chuỗi được định nghĩa là các chuỗi ký tự được theo sau bởi một byte rỗng (một byte đầy đủ của tất cả các số 0 ở dạng nhị phân hoặc %00 trong mã hóa URL). Không có cách nào để kiểm tra độ dài của một chuỗi ngoài việc lặp lại nó cho đến khi tìm thấy một byte rỗng. Có nghĩa là khi gặp %00(byte rỗng) thì sẽ kết thúc một chuỗi. 

Có thể lợi dụng điều kiện này để loại bỏ việc kiểm tra phần mở rộng tệp bằng cách chèn %00 trước phần mở rộng tệp để hệ điều hành không xử lý tên tệp đầy đủ 

Bước 5: Thử với đường dẫn: **/image?filename=../../../etc/passwd%00TranTuanMinh.png**. Ta thu được danh sách mật khẩu

![image](https://user-images.githubusercontent.com/74781135/203584904-2f38db07-7155-4ca1-bbe1-c492585bb1f2.png)

