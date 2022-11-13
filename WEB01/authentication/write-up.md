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

Bước 7: Nhập username=apple và password=pepper vào để hoàn thành bài lab
![image](https://user-images.githubusercontent.com/74781135/201257256-96db7564-c93b-404c-8f58-ae10341de6fe.png)

## Lab5: Username enumeration via response timing
Bước 1: Đăng nhập với username và password ngẫu nhiên và chặn batwss post request này. Gửi request đến Repeater
![image](https://user-images.githubusercontent.com/74781135/201501372-cd35d024-3060-48eb-b937-68768ecd534e.png)

Bước 2: Thêm trường X-Forwarded-For vào header để phá vỡ cơ chế block ip
![image](https://user-images.githubusercontent.com/74781135/201501546-9e943b19-70a7-4023-95bf-59900e307bcb.png)

Bằng cách sử dụng bộ lặp với username chính xác là "wiener" và mật khẩu có độ dài khác nhau có thể thấy rằng mật khẩu càng dài thì thởi gian phản hồi càng tăng. 

Bước 3: Gửi request đến Intruder, chọn kiểu tấn công là Pitchfork. Thêm payload ở X-Forwarded-For và username và đặt một mật khẩu dài
![image](https://user-images.githubusercontent.com/74781135/201501772-5f8f17b5-fc56-4438-94a6-4be111d834aa.png)

Bước 4: Ở tab Payloads, đổi Payload type sang Numbers. Nhập khoảng từ 1 đến 100 và chọn step=1. Đặt Max fraction digits=0, điều này sẽ giúp giả mạo ip
![image](https://user-images.githubusercontent.com/74781135/201501968-9be91be4-e69d-4ee4-9862-b8e28e4c486a.png)

Bước 5: Thêm danh sách username ở payload thứ 2 và tiến hành tấn công
![image](https://user-images.githubusercontent.com/74781135/201502008-e45eb2b7-4e41-4762-b36c-ce069af8c98d.png)

Bước 6: Để xem username nào đúng cần kiểm tra thời gian phản hồi. Ở cửa sổ tấn công chọn Columns và chọn Response received, Response completed

![image](https://user-images.githubusercontent.com/74781135/201502640-31c90c64-317b-4c37-b1ac-799f70ebe4ca.png)

Bước 7: Sử dụng username=ak để brute-force password. Các bước tương tự như trước, chọn tham số tấn công là password. Phản hồi 302 sẽ là password đúng
![image](https://user-images.githubusercontent.com/74781135/201502752-9d77a705-bc5a-4a93-8d43-ae35113bd082.png)

Bước 8: Nhập username=ak và password=123456 vào để hoàn thành bài lab
![image](https://user-images.githubusercontent.com/74781135/201502771-d788d6b2-62f6-436f-90ff-605003db266c.png)

## Lab6: Broken brute-force protection, IP block
Bước 1: Thử sau 4 lần đăng nhập không thành công, địa chỉ IP đã bị chặn
![image](https://user-images.githubusercontent.com/74781135/201504128-29c0013c-111e-4527-b529-54fa3dd763e3.png)

Bước 2: Tạo danh sách tài khoản và mật khẩu mới

![image](https://user-images.githubusercontent.com/74781135/201504445-a2c21b35-3538-4729-9de2-30e5db510bb0.png)
![image](https://user-images.githubusercontent.com/74781135/201504424-aaf1a14b-6f55-41dc-be3e-63b4c3a21952.png)

Bước 3: Bắt request login và gửi đến Intruder. Đặt payload tại username và password. Thêm danh sách tài khoản và mật khẩu mới vừa tạo vào lần lượt cho username và password sau đó tiến hành tấn công

![image](https://user-images.githubusercontent.com/74781135/201504562-7f573008-2cec-4b76-99c9-efce400ac78f.png)
![image](https://user-images.githubusercontent.com/74781135/201504582-f1ac7bb3-df05-49aa-931d-b240fef44f9e.png)

## Lab7: Username enumeration via account lock
Bước 1: Gửi POST /login request đến Intruder
Bước 2: Chọn kiểu tấn công Cluster bomb. Thêm payload vào username và vào cuối request body
![image](https://user-images.githubusercontent.com/74781135/201515176-f6164cb6-7cab-49a2-9728-ee0d71f1d1d0.png)
Bước 3: Ở tab Payloads, thêm danh sách username vào payload đầu tiên. Payload thứ hai chọn Null Payloads vào chọn tùy chọn để tạo 5 payloads và tiến hành tấn công
![image](https://user-images.githubusercontent.com/74781135/201515295-dd811a9d-de21-4a79-b5f9-c669f6710692.png)
![image](https://user-images.githubusercontent.com/74781135/201515323-a3c07194-5fe8-49ed-9085-ea379c8690f3.png)
Bước 4: Có một username có phản hồi dài hơn các username khác và trả ra một thông báo lỗi khác. Lưu lại username này
![image](https://user-images.githubusercontent.com/74781135/201515537-a937f1ed-0a36-4161-9bab-df3ea260c142.png)

Bước 5:  Sử dụng username=agenda để brute-force password. Có một phản hồi không thông báo lỗi. Đấy là mật khẩu cần tìm
![image](https://user-images.githubusercontent.com/74781135/201515673-6aa6154a-8a48-4faf-a7a0-30c5de8901c6.png)

Bước 6: Nhập username=agenda, password=12345 vào và hoàn thành bài lab
![image](https://user-images.githubusercontent.com/74781135/201515720-e09834d1-41e4-49cf-b549-61d3f883341a.png)

## Lab2: 2FA simple bypass
Bước 1: Truy cập vào tài khoản của mình. Chọn Email Client để lấy mã.
