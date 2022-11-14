# Access control
## CÁC BÀI LAB ĐÃ HOÀN THÀNH
Đã hoàn thành tất cả các bài lab thuộc phần Access Control
## Vertical privilege escalation
**Lab1: Unprotected admin functionality**

Bước 1: Truy cập vào robots.txt

![image](https://user-images.githubusercontent.com/74781135/201593383-b178cbcb-1853-49a8-8384-25759294ff99.png)

Bước 2: Sử dụng /administrator-panel để truy cập vào trang admin
![image](https://user-images.githubusercontent.com/74781135/201593693-2d740fd1-df70-40c8-bb3a-64bb127f9a85.png)

Bước 3: Xóa user carlos để hoàn thành bài lab
![image](https://user-images.githubusercontent.com/74781135/201593796-fdac268e-4f61-436e-834c-a0129afb8f37.png)

**Lab2: Unprotected admin functionality with unpredictable URL**

Bước 1: View details một sản phẩm bất kỳ, bắt request đó và gửi đến Repeater

Bước 2: Trong Repeater gửi request một lần nữa. Ở tab Response lấy được endpoint truy cập vào trang admin
![image](https://user-images.githubusercontent.com/74781135/201595419-a410122d-3ede-439e-81f2-236d1772ba86.png)

Bước 3: Truy cập vào trang admin xóa username carlos để hoàn thành bài lab
![image](https://user-images.githubusercontent.com/74781135/201595583-f3964577-a94b-4b3d-9eac-8336c4314544.png)

**Lab3: User role controlled by request parameter**

Bước 1: Login vào tài khoản
![image](https://user-images.githubusercontent.com/74781135/201599097-d858b0df-632a-4527-bd06-dea11c8e12f7.png)

Bước 2: Chỉnh sửa cookie thành Admin=true và reload lại web
![image](https://user-images.githubusercontent.com/74781135/201599272-a7d7bfcc-a3ca-48cf-890f-bec3fb8a8d86.png)

Bước 3: Truy cập vào /admin xóa user carlos để hoàn thành bài lab
![image](https://user-images.githubusercontent.com/74781135/201599512-582d91a5-5225-4971-96b7-edbc31c234bf.png)

**Lab4: User role can be modified in user profile**

Bước 1: Login vào tài khoản, chọn update email
![image](https://user-images.githubusercontent.com/74781135/201601101-6f4bc0ad-de1f-4443-b2df-d67699857ac8.png)

Bước 2: Bắt request và gửi đến Repeater

Bước 3: Thêm "roleid": 2 vào JSON payload và gửi lại request. Thấy response trả về có "roleid": 2 chính là quyền admin
![image](https://user-images.githubusercontent.com/74781135/201601998-d8a8ada0-011a-4cff-9ce2-bc8913840988.png)

Bước 4: Quay lại trình duyệt truy cập vào /admin xóa user carlos để hoàn thành bài lab
![image](https://user-images.githubusercontent.com/74781135/201602146-d44ab8d9-c32c-4a2d-8719-8b11112bca6c.png)

**Lab10: URL-based access control can be circumvented**

Bước 1: Thử truy cập vào /admin thì nhận được thông báo "Access denied"

Bước 2: Load lại và bắt request gửi đến Repeater

Bước 3: Sửa URL thành GET / HTTP/1.1 và thêm HTTP header X-Original-URL: /admin sau đó gửi request thì truy cập được trang admin
![image](https://user-images.githubusercontent.com/74781135/201672199-90991fe8-5153-4ebd-b36a-ca60f7ef5c37.png)

Bước 4: Thêm query parameter: username=carlos và sửa X-Original-URL: /admin/delete. Kết quả user carlos bị xóa, bài lab hoàn thành
![image](https://user-images.githubusercontent.com/74781135/201673008-0ee3e15c-b7cb-45e7-8dcc-d4caf70a8fd4.png)

**Lab11: Method-based access control can be circumvented**

Bước 1: Login vào tài khoản administrator. Chọn Admin panel. Thử nâng quyền user carlos, bắt request này và gửi đến Repeater
![image](https://user-images.githubusercontent.com/74781135/201679053-f4730fe3-b320-4179-9c66-329a0b6edd14.png)

Bước 2: Đăng nhập vào tài khoản wiener và truy cập vào trang Home. Bắt request này và gửi đến Repeater
![image](https://user-images.githubusercontent.com/74781135/201684797-be08b0fc-c1f6-4b0c-be29-e308b6eea0d8.png)

Bước 3: Sửa request POST nâng quyền thành GET, copy cookie của wiener vào và gửi request
![image](https://user-images.githubusercontent.com/74781135/201685098-de84c2be-344e-49c9-9b01-2b514e56a217.png)

Bài lab được hoàn thành
![image](https://user-images.githubusercontent.com/74781135/201685253-ac5edecb-0e37-44c4-9949-5d8030452dab.png)

## Horizontal privilege escalation
**Lab5: User ID controlled by request parameter**

Bước 1: Login vào tài khoản được cung cấp
![image](https://user-images.githubusercontent.com/74781135/201621875-38003893-e786-4cd8-a8a6-562a2c824ef9.png)

Bước 2: Click my acccount, bắt request này và sửa wiener thành carlos và click forward
![image](https://user-images.githubusercontent.com/74781135/201623479-cec78664-f864-448d-8d92-806484d1d512.png)

Bước 3: Truy cập được vào user carlos, copy API key nộp để hoàn thành bài lab
![image](https://user-images.githubusercontent.com/74781135/201623871-e9632f80-bebe-4f7b-b037-c2c4a4f7fa74.png)

**Lab6: User ID controlled by request parameter, with unpredictable user IDs**

Bước 1: Vào blog của carlos và lấy GUID từ URL

![image](https://user-images.githubusercontent.com/74781135/201627224-306b9056-2f6e-432f-848f-ecf342a84ec1.png)

Bước 2: Đăng nhập vào wiener và thay đổi URL thành

![image](https://user-images.githubusercontent.com/74781135/201627613-ab91a08b-d92a-43f3-a473-70a917e0adbc.png)

Bước 3: Truy cập thành công vào carlos. Submit api key để hoàn thành bài lab
![image](https://user-images.githubusercontent.com/74781135/201627858-3f98fcb4-8950-4c0d-937d-68dc4de10b66.png)

**Lab7: User ID controlled by request parameter with data leakage in redirect**

Bước 1: Đăng nhập vào wiener, bắt request và gửi đến Repeater
![image](https://user-images.githubusercontent.com/74781135/201635675-58c81830-f8a7-47e1-8f7c-799aa3faa113.png)

Bước 2: Trong Repeater sửa id=carlos và gửi lại. Trong Response có chứa API key của carlos
![image](https://user-images.githubusercontent.com/74781135/201635998-d4eab0d2-cb05-4b7b-b16f-c970141a1923.png)

Bước 3: Submit API key để hoàn thành bài lab
![image](https://user-images.githubusercontent.com/74781135/201636969-816a4aab-5f17-494b-8493-6e32847b00da.png)

## Horizontal to vertical privilege escalation
**Lab8: User ID controlled by request parameter with password disclosure**

Bước 1: Login và wiener. Bắt request gửi đến Repeater
![image](https://user-images.githubusercontent.com/74781135/201664921-60f0e2fe-7e01-4733-a0f5-3e669c31808e.png)

Bước 2: Trong Repeater, sửa id=administrator và gửi request. Ở response lấy được password của administrator
![image](https://user-images.githubusercontent.com/74781135/201665384-4569975c-e952-4932-bc24-e56f6b9da804.png)

Bước 3: Đăng nhập tài khoản administrator và xóa user carlos. Bài lab được hoàn thành
![image](https://user-images.githubusercontent.com/74781135/201665758-a1cbfae1-9f39-42d6-a773-c10f02190a53.png)

## Insecure direct object references (IDOR)
**Lab9: Insecure direct object references**

Bước 1: Chọn Live chat

Bước 2: Gửi lời nhắn và chọn View transcript

Bước 3: Bắt request và nhận thấy tên file được đánh số tăng dăn
![image](https://user-images.githubusercontent.com/74781135/201667383-77a21535-56b6-4672-81ec-c88f14dc2d39.png)

Bước 4: Đổi tên file thành 1.txt và xem nội dung file
![image](https://user-images.githubusercontent.com/74781135/201668422-48bbe069-e861-4954-898e-3e273dbb2f19.png)

Bước 5: Đăng nhập tài khoản carlos với password thu được trong file 1.txt
![image](https://user-images.githubusercontent.com/74781135/201668718-cfb70961-7d24-402a-ad87-27f0288b9a99.png)

## Access control vulnerabilities in multi-step processes
**Lab12: Multi-step process with no access control on one step**

Bước 1: Đăng nhập tài khoản quản trị viên

Bước 2: Nâng quyền user carlos, bắt request xác nhận và gửi đến Repeater
![image](https://user-images.githubusercontent.com/74781135/201692609-ed81f107-b89e-4c88-8c5d-48e3e660ecfe.png)

Bước 3: Đăng nhập vào tài khoản wiener. Bặt request truy cập đến trang home và gửi đến Repeater. Copy cookie
![image](https://user-images.githubusercontent.com/74781135/201693994-dbb6fbab-e90e-4bef-a93f-3961a6cca85a.png)

Bước 4: Thay thế cookie ở request xác nhận nâng quyền bằng cooki của wiener, sửa username=wiener và gửi request thấy thông báo thành công
![image](https://user-images.githubusercontent.com/74781135/201694222-611197a0-2a30-426b-8fff-0db4cf9b9985.png)

Bài lab được hoàn thành
![image](https://user-images.githubusercontent.com/74781135/201694357-76292add-d268-4318-8801-5e8712bb1a16.png)

**Lab13: Referer-based access control**

Bước 1: Đăng nhập vào tài khoản quản trị viên 

Bước 2: Nâng quyền user carlos, bắt requets và gửi đến Repeater

Trong HTTP header có Referer, ta thử xóa đi thì thấy lỗi "Unauthorized".

Đăng nhập với tài khoản wiener rồi sửa URL thành /admin-roles?username=wiener&action=upgrade, cùng với HTTP header "Referer: https://0a80009c03787d3bc033792e003400b1.web-security-academy.net/admin". Sau khi gửi, kết quả thành công
![image](https://user-images.githubusercontent.com/74781135/201699628-1c428b9c-34ed-4396-bae6-bd05161c475d.png)

![image](https://user-images.githubusercontent.com/74781135/201699734-0617150a-eada-4449-8a9d-fdb934ff1265.png)


