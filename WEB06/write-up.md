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

