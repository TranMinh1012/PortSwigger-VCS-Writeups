# XML external entity (XXE) injection
## Exploiting XXE to retrieve files
**Lab 1: Exploiting XXE using external entities to retrieve files**

Bước 1: Truy cập một sản phẩm bất kỳ và chọn `Check stock`

Bước 2: Gửi request đến Repeater

![image](https://user-images.githubusercontent.com/74781135/209254747-bafe5abd-0436-4a90-819d-4ff7cedd794a.png)

Bước 3: Chỉnh sửa request để lấy được danh sách mật khẩu

![image](https://user-images.githubusercontent.com/74781135/209254991-3ac8e791-fa53-44ae-859d-dc57cd9b40f9.png)

Bài lab được hoàn thành

![image](https://user-images.githubusercontent.com/74781135/209255038-804b3a08-eb96-4ca2-809c-9cec189c1ada.png)

## Exploiting XXE to perform SSRF attacks
**Lab 2: Exploiting XXE to perform SSRF attacks**

Bước 1: Truy cập một sản phẩm bất kỳ và chọn `Check stock`

Bước 2: Gửi request đến Repeater, chỉnh sửa request

![image](https://user-images.githubusercontent.com/74781135/209257673-e3122f89-6933-4d79-8166-2b06dabd61b5.png)

![image](https://user-images.githubusercontent.com/74781135/209257730-f59ddb52-5bb9-469d-85a7-8ccbc74ffdc0.png)

![image](https://user-images.githubusercontent.com/74781135/209257851-0279d271-aef9-43e9-8486-598f0bac1a6a.png)

![image](https://user-images.githubusercontent.com/74781135/209257906-39b9250b-bc15-4ee2-aa71-df40425c4c52.png)

![image](https://user-images.githubusercontent.com/74781135/209258305-64ab3515-dc46-4ff6-a178-f72e788b3438.png)

![image](https://user-images.githubusercontent.com/74781135/209258160-cb0ba15f-e50f-4cee-af31-ee214ec4989b.png)

Bài lab được hoàn thành 

![image](https://user-images.githubusercontent.com/74781135/209258216-57117826-4a83-4c2b-a8b2-ae1a29137357.png)

## Detecting blind XXE using out-of-band (OAST) techniques
**Lab 3: Blind XXE with out-of-band interaction**

Bước 1: Truy cập một sản phẩm bất kỳ và chọn `Check stock`

Bước 2: Gửi request đến Repeater, chỉnh sửa request

![image](https://user-images.githubusercontent.com/74781135/209263726-80573e60-59db-4c07-9b41-b667ab3d4270.png)

Phía Burp Collaborator xuất hiện 1 số tương tác DNS và HTTP

![image](https://user-images.githubusercontent.com/74781135/209264053-49340cc1-87aa-4686-9cd8-1793a9229252.png)

Bài lab được hoàn thành

![image](https://user-images.githubusercontent.com/74781135/209264142-f8ad659f-e7d6-4134-b273-645b84bdaee3.png)

**Lab 4: Blind XXE with out-of-band interaction via XML parameter entities**

Bước 1: Truy cập một sản phẩm bất kỳ và chọn `Check stock`

Bước 2: Gửi request đến Repeater, chỉnh sửa request

![image](https://user-images.githubusercontent.com/74781135/209294971-b9b23758-b984-4450-a784-a263b659980c.png)

Phía Burp Collaborator xuất hiện 1 số tương tác DNS và HTTP

![image](https://user-images.githubusercontent.com/74781135/209295117-0af45e2b-7812-4f7a-a709-de027d097244.png)

Bài lab được hoàn thành 

![image](https://user-images.githubusercontent.com/74781135/209295225-677ee5e8-2b75-41b9-919f-5111e1c9d5ae.png)

## Exploiting blind XXE to exfiltrate data out-of-band
**Lab 5: Exploiting blind XXE to exfiltrate data using a malicious external DTD**

Bước 1: Truy cập một sản phẩm bất kỳ và chọn `Check stock`

Bước 2: Tạo một file DTD trên exploit server

![image](https://user-images.githubusercontent.com/74781135/209417272-bee1b72f-5eb2-43a2-8196-47551b6b4484.png)

Bước 3: Chỉnh sửa request

![image](https://user-images.githubusercontent.com/74781135/209417346-0519051f-b621-4720-bbf1-cecab8f5af28.png)

Sau khi gửi request độc hại, các request được ghi lại trên exploit server

![image](https://user-images.githubusercontent.com/74781135/209417361-1f6d66ad-cff7-4180-8145-b50353c0260d.png)

Đầu tiên là ứng dụng tải file DTD độc hại, thứ 2 là đánh cắp tên máy chủ

Bài lab được hoàn thành

![image](https://user-images.githubusercontent.com/74781135/209417418-e527175c-5329-480d-9c3c-3fcdcb08d88b.png)

## Exploiting blind XXE to retrieve data via error messages
**Lab 6: Exploiting blind XXE to retrieve data via error messages**

Bước 1: Truy cập một sản phẩm bất kỳ và chọn `Check stock`

Bước 2: Tạo một file DTD trên exploit server

![image](https://user-images.githubusercontent.com/74781135/209417879-e0936e2a-4284-4ba6-ac70-b93c8d28fcaa.png)

Bước 3: Chỉnh sửa request

![image](https://user-images.githubusercontent.com/74781135/209417904-6ee2d57c-563b-48de-82a4-70a7c1a34e9e.png)

Bài lab được hoàn thành 

![image](https://user-images.githubusercontent.com/74781135/209417919-a6ef59f2-6a1d-46f4-a30d-1758112b5993.png)

## XInclude attacks
**Lab 7: Exploiting XInclude to retrieve files**

Bước 1: Truy cập một sản phẩm bất kỳ và chọn `Check stock`. Gửi request đến Repeater

![image](https://user-images.githubusercontent.com/74781135/209418390-ef4e9e8f-787d-4547-900a-6b2e64df1248.png)

Có thể thấy lần này yêu cầu không phải là XML. Ví dụ kiết quả được nhúng trong XML document như sau

`<?xml version="1.0" encoding="UTF-8"?>
<stockCheck>
  <productId>1</productId>
  <storeId>1</storeId>
</stockCheck> `

Nếu như có một DTD được định nghĩa cho XML document thì những thay đổi đối với XML document sẽ không được thông qua.

Bước 2: Sử dụng XInclude để xây dựng một XML document mới. Giống như trong các phòng thí nghiệm trước, `productId` được lặp lại nếu nó không hợp lệ.

![image](https://user-images.githubusercontent.com/74781135/209419123-2192a22a-12d8-4653-9a38-27ef03543d19.png)

Bài lab được hoàn thành 

![image](https://user-images.githubusercontent.com/74781135/209419133-32f3da1b-7562-4dd8-872b-df42b1cbfcde.png)

## XXE attacks via file upload
**Lab 8: Exploiting XXE via image file upload** (Có tham khảo solution)

Bước 1: Truy cập vào một blog và post

Bước 2: Tạo một ảnh SVG với nội dung

![image](https://user-images.githubusercontent.com/74781135/209419408-79f88e4e-c027-408c-b14d-7ef1c27a36e1.png)

Bước 3: Sử dụng ảnh vừa tạo làm avatar và post commnet

![image](https://user-images.githubusercontent.com/74781135/209419617-32f231a7-2746-4103-88a0-2699e67a27a2.png)

Nội dung của file /etc/hostname ở trong ảnh

![image](https://user-images.githubusercontent.com/74781135/209419550-e0c1d290-2acc-4644-be48-4d0d71691ab1.png)

Bài lab được hoàn thành

![image](https://user-images.githubusercontent.com/74781135/209419588-1d853221-21c5-44cb-ba61-1b7d4cebe22d.png)

