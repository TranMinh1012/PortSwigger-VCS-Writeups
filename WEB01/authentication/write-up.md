# Authentication
## Lab1: Username enumeration via different responses
Bài lab này dễ bị tấn công trước các cuộc tấn công tên người dùng và các cuộc tấn công brute-force. Nó có một tài khoản có tên người dùng và mật khẩu có thể dự đoán được, có thể được tìm thấy trong các danh sách.

Bước 1: Click chọn My account để chuyển sang giao diện đăng nhập.

Bước 2: Bật Intercept trên Burp và nhập ngẫu nhiên một username và password ở giao diện đăng nhập, sau đó click Log in
![image](https://user-images.githubusercontent.com/74781135/201239248-b19b1b83-9f66-4577-92a3-5b116a3cf2dc.png)

Bước 3: Trên Burp bắt được request. Gửi request đó đến Intruder
![image](https://user-images.githubusercontent.com/74781135/201239639-0a99d596-918e-43a6-b5fe-92475546cf57.png)
![image](https://user-images.githubusercontent.com/74781135/201239928-5d0e13ed-3e22-4ec0-b3a9-9c4fda6871ba.png)

Bước 4: Ở Intruder, clear toàn bộ payloads sau đó add payloads ở vị trí username
![image](https://user-images.githubusercontent.com/74781135/201240311-cd21ea5a-e1ac-4494-9a20-2579e82c93c0.png)

Bước 5: Tại tab Payloads, paste danh sách username vào và chọn Start attack để bắt đầu tấn công
![image](https://user-images.githubusercontent.com/74781135/201240876-144b611f-f558-417a-923e-595286a6e2e1.png)

Bước 6: Ở tab Results, có một request có length dài hơn các request còn lại, đấy chính là username hợp lệ
![image](https://user-images.githubusercontent.com/74781135/201242733-fad3e17f-c04a-4939-ad3d-9b9aa525690d.png)

Bước 7: Thay giá trị của username=af và tiến hành quá trình tìm password hợp lệ tương tự như đối với username, ta tìm được password hợp lệ
![image](https://user-images.githubusercontent.com/74781135/201243509-4a045929-aa33-42dd-aba0-2faf424145c3.png)

Bước 8: Nhập username và password hợp lệ vào và click Log in. Bài lab được hoàn thành
![image](https://user-images.githubusercontent.com/74781135/201243668-8d65cb2f-5637-465b-a09c-28782f295ccc.png)

## Lab4: Username enumeration via subtly different responses
Bước 1: Đăng nhập với username và password ngẫu nhiên và chặn bắt post request này. Gửi request đến Intruder và add payloads ở tham số username
![image](https://user-images.githubusercontent.com/74781135/201254362-fe419613-da58-4645-8360-ef233f5f2a76.png)

Bước 2: Ở tab Payloads, chọn Payload type : Sumple list và thêm danh sách username vào
![image](https://user-images.githubusercontent.com/74781135/201254649-fae7211f-b26c-4212-b04f-e21a1bb6771c.png)

Bước 3: Ở tab Options, trong Grep-Extract, click Add. Trong hộp thoại xuất hiện, cuộn xuống qua phản hồi cho đến khi tìm thấy thông báo lỗi "Invalid username or password." Bôi đen thông báo và click OK
![image](https://user-images.githubusercontent.com/74781135/201255260-c896781f-8632-42e2-9b69-693abd68ec89.png)

Bước 4: Thông báo lỗi đã được thêm vào. Quay lại Payloads và click Start attack
![image](https://user-images.githubusercontent.com/74781135/201255548-8b9e937e-2a2b-48c2-9141-dc2f44d698dc.png)

Bước 5: username apple hiển thị thông báo lỗi không đầy đủ. Thiếu dấu "." ở cuối cùng. Lưu lại username này
![image](https://user-images.githubusercontent.com/74781135/201256492-a452cb51-c880-4dbc-9d2b-e82dad9171c9.png)

Bước 6: Sử dụng username=apple để brute-force password. Các bước tương tự như trước, chọn tham số tấn công là password. phản hồi 302 sẽ là password đúng
![image](https://user-images.githubusercontent.com/74781135/201257079-1b0e3fa5-74f9-44b9-a8f4-52f036152f6c.png)

Bước 7: Nhập username=apple và password==pepper vào để hoàn thành bài lab
![image](https://user-images.githubusercontent.com/74781135/201257256-96db7564-c93b-404c-8f58-ae10341de6fe.png)
