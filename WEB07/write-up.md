# Cross-site scripting
## Reflected XSS
**Lab: Reflected XSS into HTML context with nothing encoded**

Bước 1: Thử tìm kiếm với một từ bất kỳ

![image](https://user-images.githubusercontent.com/74781135/210736351-26b9b0c8-248a-4fee-a3b9-7e6018063c9b.png)

![image](https://user-images.githubusercontent.com/74781135/210736468-f609c800-26f0-4c76-b75e-a6b4ec6f01e3.png)

Có thể thấy giá trị tìm kiếm hiển thị ở phần response trong thẻ h1

Bước 2: Nhập `<script>alert(1)</script>` và tìm kiếm. Bài lab được hoàn thành

![image](https://user-images.githubusercontent.com/74781135/210737036-e039c011-3402-4974-bb1d-b4c0d74a580b.png)

## Stored XSS
**Lab: Stored XSS into HTML context with nothing encoded**

Bước 1: Vào một blog bất kỳ và post commnet với nội dung `<script>alert(1)</script>`

Bài lab được hoàn thành

![image](https://user-images.githubusercontent.com/74781135/210740078-2780169f-a52e-4037-b632-f31db441740a.png)

## DOM-based XSS
