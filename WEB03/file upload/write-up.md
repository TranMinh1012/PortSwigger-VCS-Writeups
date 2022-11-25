# File Upload Vulnerabilities
## Exploiting unrestricted file uploads to deploy a web shell
**Lab 1: Remote code execution via web shell upload**

Bước 1: Login vào tài khoản được cung cấp và thay đổi avatar thì thấy avatar đã được cập nhật thành công

![image](https://user-images.githubusercontent.com/74781135/203885601-a7b9afee-98b4-4fe5-a75b-1a685dee2a90.png)

![image](https://user-images.githubusercontent.com/74781135/203885633-e5b2c02e-fc47-495f-8b68-9aedb7aef8fa.png)

Bước 2: Thử tải lên một file test.txt thì có thể thấy ứng dụng vẫn chấp nhận upload

![image](https://user-images.githubusercontent.com/74781135/203885904-2092666e-b715-4730-a56c-b994cefc93af.png)

Bước 3: Vào Proxy > HTTP history, tìm đến request method POST vừa up file test.txt và gửi đến Repeater

![image](https://user-images.githubusercontent.com/74781135/203886433-bb4cdc17-34a4-4621-acc6-000ec49f64b5.png)

Bước 4: Trong Repeater, thay đổi filename="exploit.php" và nội dung thành: `<?php echo file_get_contents('/home/carlos/secret'); ?>`

![image](https://user-images.githubusercontent.com/74781135/203886762-d0da75cf-8fdf-4117-b8ce-a05f313e985f.png)

Bước 5: Vào Proxy > HTTP history, tìm đến request method GET sau khi POST thành công file test.txt và gửi đến Repeater

![image](https://user-images.githubusercontent.com/74781135/203886991-9e20af56-a170-43a1-94f6-72bafeb82f82.png)

Bước 6: Trong Repeater, thay đổi đường dẫn đến file exploit.php và gửi request thì sẽ lấy được nội dung của **/home/carlos/secret**

![image](https://user-images.githubusercontent.com/74781135/203887282-72561267-2b03-42a9-be18-c4d7a9580e44.png)

Bước 7: Submit để hoàn thành bài lab

![image](https://user-images.githubusercontent.com/74781135/203887377-0499847b-c9da-4267-b35f-b72ee6dc0816.png)

## Exploiting flawed validation of file uploads
**Lab 2: Web shell upload via Content-Type restriction bypass**

Bước 1: Login vào tài khoản được cung cấp và thử tải lên một file test.txt làm avatar thì thấy không được phép tải lên

![image](https://user-images.githubusercontent.com/74781135/203892112-736731b1-10d7-41cf-b6c6-ea4328c0ba35.png)

Bước 2: Vào Proxy > HTTP history, tìm đến request method POST vừa up file test.txt và gửi đến Repeater

![image](https://user-images.githubusercontent.com/74781135/203892238-82a34b01-7a2a-4047-97e5-a5b1195ff73b.png)

Bước 3: Thay đổi nội dung trường **Content-Type: image/jpeg** và gửi lại request thì thấy file test.txt đã được upload thành công

![image](https://user-images.githubusercontent.com/74781135/203892529-d0b7c8de-d92a-41f4-9199-5d8d475da910.png)

Bước 4: Thay đổi filename="exploit.php" và nội dung thành: `<?php echo file_get_contents('/home/carlos/secret'); ?>`

![image](https://user-images.githubusercontent.com/74781135/203892659-5a41336e-c845-4134-a990-36ddae5febf7.png)

Bước 5: Tải một avatar mới lên và gửi request GET avatar đấy trong Proxy > HTTP history đến Repeater

![image](https://user-images.githubusercontent.com/74781135/203893392-68ad2686-2564-4631-b247-7a9019e96d3d.png)

Bước 6: Thay đổi đường dẫn đến file exploit.php và gửi request thì sẽ lấy được nội dung của **/home/carlos/secret**

![image](https://user-images.githubusercontent.com/74781135/203893499-70cc3cdc-8a13-4cb9-b245-7f0dddcd6882.png)

Bước 7: Submit để hoàn thành bài lab

![image](https://user-images.githubusercontent.com/74781135/203893583-c170e95e-5e28-467c-8d43-7ef24e23d3cb.png)

## Preventing file execution in user-accessible directories
**Lab 3: Web shell upload via path traversal**

Bước 1: Login vào tài khoản được cung cấp và thay đổi avatar

![image](https://user-images.githubusercontent.com/74781135/203897336-c8add284-368a-42ed-8951-dfa028ac0b4a.png)

Bước 2: Vào Proxy > HTTP history, tìm đến request method POST vừa up file ảnh và gửi đến Repeater

![image](https://user-images.githubusercontent.com/74781135/203897469-7b3b425e-4b94-4ec9-99b7-65b0ec975843.png)

Bước 3: Thay đổi filename="exploit.php" và nội dung thành: `<?php echo file_get_contents('/home/carlos/secret'); ?>`

![image](https://user-images.githubusercontent.com/74781135/203897656-e1107c0e-6ccf-4303-aec1-e5ef737f8cc6.png)

Bước 4: Truy cập đến đường dẫn file exploit.php thì thấy trả ra nội dung của file => file php không được thực thi trong đường dẫn **/files/avatars/**

![image](https://user-images.githubusercontent.com/74781135/203897769-05f2454d-c949-426f-beec-7c9361c0e65f.png)

Bước 5: Thử thoát khỏi đường dẫn xem có thực thi được file php không. Thay đổi **filename="../exploit.php"**

![image](https://user-images.githubusercontent.com/74781135/203898230-49b16cb7-640e-4884-b5f5-ead554cdcc79.png)

Xác nhận tải lên hiển thị đường dẫn giống hệt như lần tải lên trước đó, do đó, truyền tải đường dẫn không thành công:

Bước 6: Thử mã hóa `../` thành `%2e%2e%2f`. filename="%2e%2e%2f/exploit.php"

![image](https://user-images.githubusercontent.com/74781135/203898565-0f14e32d-1637-42df-b26a-3ce9cd239a59.png)

Phản hồi cho biết rằng quá trình duyệt đường dẫn đã thành công.

Bước 7: Truy cập đến đường dẫn file exploit.php và gửi request thì thấy trả ra nội dung của **/home/carlos/secret**

![image](https://user-images.githubusercontent.com/74781135/203898829-419721ca-d79b-41f4-8992-b642fd4465af.png)

Bước 8: Submit để hoàn thành bài lab

![image](https://user-images.githubusercontent.com/74781135/203898889-d8a682df-ef0e-480a-848b-b84951b13745.png)

## Insufficient blacklisting of dangerous file types
**Lab 4: Web shell upload via extension blacklist bypass**

Cách 1: Tải file có đuôi `.phtml` với nội dung `<?php echo file_get_contents('/home/carlos/secret'); ?>` 

![image](https://user-images.githubusercontent.com/74781135/204010449-6e0a642d-821b-4c8a-b75e-a71b623d50ab.png)

![image](https://user-images.githubusercontent.com/74781135/204010581-723f9eed-03e7-45fe-b612-348e03a81e22.png)

![image](https://user-images.githubusercontent.com/74781135/204010666-1308d160-47c0-4104-a1aa-6fc7493e31d9.png)

Cách 2 (Có tham khảo solution): 

Ứng dụng này sử dụng máy chủ apache, tải lên tệp .htaccess tùy chỉnh để ánh xạ phần mở rộng `.ttm` sang PHP

![image](https://user-images.githubusercontent.com/74781135/204011605-830238cc-8441-4601-8d88-b36ff97ebae5.png)

Tải file `exploit.ttm` với nội dung `<?php echo file_get_contents('/home/carlos/secret'); ?>` 

![image](https://user-images.githubusercontent.com/74781135/204011998-61efc133-91c5-4e38-bfef-be6fd507905a.png)

Gọi file exploit.ttm sẽ thực thi mã PHP và hiển thị chuỗi bí mật

![image](https://user-images.githubusercontent.com/74781135/204012561-fdd5fab5-6953-468c-a79a-1614964aa718.png)

## Obfuscating file extensions
**Lab 5: Web shell upload via obfuscated file extension**

Bước 1: Thử tải một file php lên để làm avatar thì thấy thông báo chỉ chấp nhận file jpg và png

![image](https://user-images.githubusercontent.com/74781135/204014902-de39ee9f-741e-4807-ac5e-58878524474c.png)

Bước 2: Trong Proxy > HTTP history, tìm đến request method POST vừa up file php và gửi đến Repeater

![image](https://user-images.githubusercontent.com/74781135/204015211-e9d9eee9-7256-4e12-ad27-1be49aaa50f8.png)

Bước 3: Thử tải lên tệp `exploit.php%00.jpg` (%00-byte rỗng để kết thúc tên tệp sớm) với nội dung `<?php echo file_get_contents('/home/carlos/secret'); ?>` thì thấy tải lên thành công

![image](https://user-images.githubusercontent.com/74781135/204015879-8ec62a3f-e163-4288-b537-fe4a7af7b81f.png)

Bước 4: Gọi file exploit.php sẽ thực thi mã PHP và hiển thị chuỗi bí mật

![image](https://user-images.githubusercontent.com/74781135/204016189-8076bfe2-2497-4317-b26c-1e15c7246eed.png)

Bước 5: Submit để hoàn thành bài lab

![image](https://user-images.githubusercontent.com/74781135/204016303-471ceb95-571a-45f6-b60b-09f1b873bd88.png)

## Flawed validation of the file's contents
**Lab 6: Remote code execution via polyglot web shell upload**

Bước 1: Thử tải lên một file php nhưng không thành công

![image](https://user-images.githubusercontent.com/74781135/204017747-e24ed3ef-d42f-4a5e-82c9-9bb2b18e03c5.png)

Bước 2: Có thể thấy việc tải lên file php chứa đoạn mã để thực thi là không được. Thử tạo ra một file hình ảnh giả mạo có chứa đoạn mã thực thi. Thử tạo file PNG giả mạo. Một số tệp tự nhận dạng bằng cách bắt đầu bằng một chữ ký cố định. Đối với PNG:

![image](https://user-images.githubusercontent.com/74781135/204018864-e38f7607-b35c-40b5-bbf2-d800e2e3ce80.png)

Nếu quá trình xác thực chỉ kiểm tra chữ ký này, có thể bỏ qua nó bằng cách bắt đầu tệp của với tám byte này.

Bước 3: Convert `<?php echo file_get_contents('/home/carlos/secret'); ?>` sang dạng HEX

![image](https://user-images.githubusercontent.com/74781135/204019347-98c89402-0c6e-4b2f-85bf-0635039fea2e.png)

Bước 4: Chèn 8 byte vào và chuyển đổi lại

![image](https://user-images.githubusercontent.com/74781135/204020018-70571c30-f1f5-4784-9cad-8fb39f87ef6d.png)

Bước 5: Tải lên file exploit.php với nội dung vừa được chuyển đổi




