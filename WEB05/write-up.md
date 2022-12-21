# Server-side request forgery (SSRF)
## SSRF attacks against the server itself
**Lab 1: Basic SSRF against the local server**

Bước 1: Truy cập vào một sản phẩm bất kỳ vào kiểm tra xem sản phẩm ý còn bao nhiêu trong kho

![image](https://user-images.githubusercontent.com/74781135/208813100-d0d6bed3-67d6-4826-ad18-cd544e303c70.png)

Bước 2: Chặn request POST kiểm tra số lượng sản phẩm trong kho

![image](https://user-images.githubusercontent.com/74781135/208815913-bb2d5445-2130-48a8-b636-96a81a3ce9bf.png)

Bước 3: Thay đổi URL

![image](https://user-images.githubusercontent.com/74781135/208816208-f44f8f85-4cdd-4a08-ab67-072de6acace0.png)

![image](https://user-images.githubusercontent.com/74781135/208816379-655b8d44-ea32-4dd3-a543-d70bd8dbc2c4.png)

Bước 4: Thử xóa user carlos thì không xóa được

![image](https://user-images.githubusercontent.com/74781135/208816628-13a71c01-04f8-4483-bc1c-ed0fcf5ff15d.png)

Bước 5: Truy cập admid panel bằng URL khác

![image](https://user-images.githubusercontent.com/74781135/208817044-a1906b10-bf86-48d4-b914-30dd38e482da.png)

Bước 6: Thay đổi URL để xóa user carlos 

![image](https://user-images.githubusercontent.com/74781135/208817199-dfca6b5b-62f3-403a-b629-63c32b5c6518.png)

Bước 7: Bài lab được hoàn thành

![image](https://user-images.githubusercontent.com/74781135/208817495-1e119006-0eaf-444a-8304-9aed5df2d6d7.png)

