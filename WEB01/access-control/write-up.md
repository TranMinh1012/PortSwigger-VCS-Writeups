# Access control
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

Bước 1: Bắt request truy cập vào trang admin và gửi tới Repeater
![image](https://user-images.githubusercontent.com/74781135/201606328-4c7a5b91-4250-4e21-be64-889dfda72a78.png)

Bước 2: Thay đổi URL thành GET / HTTP/1.1 và thêm trường X-Original-URL: /admin

**Lab11: Method-based access control can be circumvented**
