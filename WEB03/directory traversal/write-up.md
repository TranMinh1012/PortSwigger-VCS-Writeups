# Directory Traversal
## Reading arbitrary files via directory traversal
**Lab: File path traversal, simple case**

Bước 1: Truy cập vào một sản phẩm bất kỳ và bắt request đấy

Bước 2: Forward đến khi thấy được đường dẫn lấy ảnh của sản phẩm

![image](https://user-images.githubusercontent.com/74781135/203206978-90662905-73d5-48b8-9bb6-98cafa182b74.png)

Bước 3: Gửi request này đến repeater và sửa đổi đường dẫn thành **/image?filename=../../../etc/passwd**. Gửi request thì phản hồi sẽ thu được danh sách mật khẩu

![image](https://user-images.githubusercontent.com/74781135/203207160-d77230a7-1da0-4499-aece-d4945caf0dd5.png)

## Common obstacles to exploiting file path traversal vulnerabilities
**Lab: File path traversal, traversal sequences blocked with absolute path bypass**

Bước 1: Truy cập vào một sản phẩm bất kỳ vào bắt request

Bước 2: Forward đến khi thấy được đường dẫn lấy ảnh của sản phấm

![image](https://user-images.githubusercontent.com/74781135/203208697-54e747ed-40b8-44f9-af3e-06d34d1b5aa6.png)

Bước 3: Gửi request này đến repeater và sửa đổi đường dẫn thành **/image?filename=/etc/passwd**. Gửi request thì phản hồi sẽ thu được danh sách mật khẩu

![image](https://user-images.githubusercontent.com/74781135/203208854-232c527b-c42c-49ad-a669-d0225b99770a.png)

**Lab: File path traversal, traversal sequences stripped non-recursively**

Bước 1: Truy cập vào một sản phẩm bất kỳ và bắt request đấy

Bước 2: Forward đến khi thấy được đường dẫn lấy ảnh của sản phẩm

![image](https://user-images.githubusercontent.com/74781135/203211934-f8398fd4-3ca2-4e02-946c-77194b29415a.png)

Bước 3: Gửi request này đến repeater và sửa đổi đường dẫn thành **/image?filename=....//....//....//etc/passwd**. Gửi request thì phản hồi sẽ thu được danh sách mật khẩu

![image](https://user-images.githubusercontent.com/74781135/203212108-303c7d11-b7a8-48ec-b7dc-88ecd9c161ec.png)

**Lab: File path traversal, traversal sequences stripped with superfluous URL-decode**

Bước 1: Truy cập vào một sản phẩm bất kỳ và bắt request đấy

Bước 2: Forward đến khi thấy được đường dẫn lấy ảnh của sản phẩm

![image](https://user-images.githubusercontent.com/74781135/203213180-b9ed5e04-d406-4c6b-a5c2-4c446f9ecb1e.png)

Bước 3: Gửi request này đến repeater và sửa đổi đường dẫn thành **/image?filename=%252e%252e%252f%252e%252e%252f%252e%252e%252f/etc/passwd**. Gửi request thì phản hồi sẽ thu được danh sách mật khẩu

![image](https://user-images.githubusercontent.com/74781135/203213610-1e4e446a-592b-4256-a187-380e420b24e5.png)

**Lab: File path traversal, validation of start of path**

Bước 1: Truy cập vào một sản phẩm bất kỳ và bắt request đấy

Bước 2: Forward đến khi thấy được đường dẫn lấy ảnh của sản phẩm

![image](https://user-images.githubusercontent.com/74781135/203214348-1343bd52-86a4-48d7-8e4c-504a68f3cadb.png)

Bước 3: Gửi request này đến repeater và sửa đổi đường dẫn thành **/image?filename=/var/www/images/../../../etc/passwd**. Gửi request thì phản hồi sẽ thu được danh sách mật khẩu

![image](https://user-images.githubusercontent.com/74781135/203214576-034e5cb6-7960-4e91-8399-3957aaedb8ae.png)

**Lab: File path traversal, validation of file extension with null byte bypass**

Bước 1: Truy cập vào một sản phẩm bất kỳ và bắt request đấy

Bước 2: Forward đến khi thấy được đường dẫn lấy ảnh của sản phẩm

![image](https://user-images.githubusercontent.com/74781135/203215162-211250d4-5a29-42a0-8815-afc2f4958fbe.png)

Bước 3: Gửi request này đến repeater và sửa đổi đường dẫn thành **/image?filename=../../../etc/passwd%00.jpg**. Gửi request thì phản hồi sẽ thu được danh sách mật khẩu

![image](https://user-images.githubusercontent.com/74781135/203215497-f841fc8d-ab95-40f2-95b5-1c5818d38217.png)
