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
