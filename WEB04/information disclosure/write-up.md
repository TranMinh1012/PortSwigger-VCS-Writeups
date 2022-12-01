# Information Disclosure
## Error messages
**Lab1: Information disclosure in error messages**

Bước 1: Thử truy xuất đến sản phẩm có id=21

![image](https://user-images.githubusercontent.com/74781135/204840362-914e3abe-0637-42c6-947b-d71a498c1119.png)

![image](https://user-images.githubusercontent.com/74781135/204839950-76c1ae96-cbdb-419e-9af5-827561cb208c.png)

Ta thấy phản hồi không có gì bất thường

Bước 2: Thử truy xuất đến sản phẩm có id = ttminh

![image](https://user-images.githubusercontent.com/74781135/204840830-a7b09af0-2224-456f-8ea2-064fb8cbf7e4.png)

Ta nhận được phản hồi như sau

![image](https://user-images.githubusercontent.com/74781135/204841714-3bb6919c-bd91-4216-b282-b4fe8268c60b.png)

Có thể thấy trang web sử dụng **Apache Struts 2 2.3.31**

Bước 3: Nhập **2 2.3.31** để hoàn thành bài lab

![image](https://user-images.githubusercontent.com/74781135/204842980-fa5f7bab-30c2-43d7-926a-8b59af86ac5f.png)

## Debugging data
**Lab2: Information disclosure on debug page**

Bước 1: Truy cập vào một sản phẩm bất kỳ

Bước 2: Trong Proxy > HTTP history, tìm đến request method GET sản phẩm vừa chọn. Ở phía Response, có chứa một liên kết tên là "Debug" được comment lại

![image](https://user-images.githubusercontent.com/74781135/204994836-79d886b0-3e62-489d-8601-5f92eb90ef42.png)

Bước 3: Truy cập vào liên kết đó 

![image](https://user-images.githubusercontent.com/74781135/204994989-e9c2b096-2bbd-4c47-835d-fd2487cf7b40.png)

File này chứa nhiều thông tin khác nhau bao gồm `SECRET_KEY`

![image](https://user-images.githubusercontent.com/74781135/204995270-ef28c3ef-3734-45fa-a340-8c357fc601a2.png)

Bước 4: Submit `SECRET_KEY` để hoàn thành bài lab

![image](https://user-images.githubusercontent.com/74781135/204995391-76902e1a-76ee-40c4-9c56-9a8bff4cb0a4.png)

## Source code disclosure via backup files
**Lab3: Source code disclosure via backup files**

Khi phân tích một trang web, một trong những bước đầu tiên là kiểm tra sự tồn tại của file `robots.txt`

Bước 1: Thử truy cập vào file `robots.txt` ta thu được kết quả sau

![image](https://user-images.githubusercontent.com/74781135/205001411-6f34f327-39d2-4b16-b813-e2635321bd39.png)

Bước 2: Truy cập vào `/backup`. Nhận thấy có một file backup

![image](https://user-images.githubusercontent.com/74781135/205001636-6df31616-a6dc-4dc9-b57d-19deacae47c5.png)

Bước 3: Truy cập vào source code. Trong source code có chứa mật khẩu được mã hóa cứng của cơ sở dữ liệu

![image](https://user-images.githubusercontent.com/74781135/205002062-2ac630d4-41c3-46da-903b-fbd0d193612b.png)

Bước 4: Submit password để hoàn thành bài lab

![image](https://user-images.githubusercontent.com/74781135/205002241-3c6b5122-102c-4040-89b2-6a5d76f1d541.png)

## Information disclosure due to insecure configuration
**Lab4: Authentication bypass via information disclosure** (Có tham khảo solution)

Bước 1: Thử truy cập đến `/admin`

![image](https://user-images.githubusercontent.com/74781135/205004893-b9bddb90-95bd-4758-a81e-c28bc54de0d6.png)

Bước 2: Trong Proxy > HTTP history, gửi request /admin đến Repeater. Thay đổi method thành **TRACE** và gửi lại request

![image](https://user-images.githubusercontent.com/74781135/205005595-b4dd81e8-0744-4292-b034-6a26fbd6df43.png)

Trường `X-Custom-IP-Authorization` chứa địa chỉ IP. Được sử dụng để xác định xem yêu cầu có đến từ địa chỉ IP của máy chủ cục bộ hay không.

Bước 4: Vào Proxy > Options, kéo xuống phần **Match and Replace**

![image](https://user-images.githubusercontent.com/74781135/205006341-9fd88722-384a-4dc4-a955-3c615be02378.png)

Bước 5: Chọn `Add`

![image](https://user-images.githubusercontent.com/74781135/205006726-f4c9b016-5e7a-4704-8ff4-0af9f0497426.png)

Bước 6: Quay lại tranh chủ trên trình duyệt, nhận thấy đã có quyền truy cập vào admin

![image](https://user-images.githubusercontent.com/74781135/205007097-8b3b8d12-48bc-4395-8725-36af61bcf3b7.png)

Bước 7: Truy cập vào admin, xóa username carlos để hoàn thành bài lab

![image](https://user-images.githubusercontent.com/74781135/205007405-254bc1d1-3ac1-4a9e-aa63-84803e00d910.png)

## Version control history
**Lab5: Information disclosure in version control history**

Bước 1: Truy cập `/.git`

![image](https://user-images.githubusercontent.com/74781135/205010927-f30b9742-2676-4576-bc8e-6fbdc81d5e12.png)

Bước 2: Sao chép thư mục `./git` bằng wget để tạo một bản sao cục bộ

![image](https://user-images.githubusercontent.com/74781135/205013061-c3fb933e-d1d0-4e95-95bc-4fc5b2c99daf.png)

![image](https://user-images.githubusercontent.com/74781135/205013119-23c294bd-28c2-4f23-b70d-f99e6e3d33dc.png)

Bước 3: Kiểm tra git log, lần commit cuối cùng chính là xóa password của admin

![image](https://user-images.githubusercontent.com/74781135/205014465-ab0170ff-d820-474c-8ed6-56a366951c3d.png)

Bước 4: Quay lại commit đó

![image](https://user-images.githubusercontent.com/74781135/205016138-cfcac89b-4e19-42f1-820a-0149d562f1b0.png)

Bước 5: Kiểm tra nội dung của file admin.conf

![image](https://user-images.githubusercontent.com/74781135/205016656-a0ea1c3a-5374-4340-af68-5646b6449ef6.png)

Ta lấy được mật khẩu của admin

Bước 6: Đăng nhập vào tài khoản admin, xóa username carlos để hoàn thành bài lab

![image](https://user-images.githubusercontent.com/74781135/205018907-000441a5-0389-4b9c-8e7c-2c05eed67465.png)
