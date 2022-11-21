# SQL Injection
## Retrieving hidden data
**Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data**

Bước 1: Truy cập vào một category bất kỳ

Bước 2: Thêm **'+OR+1=1--** vào URL
![image](https://user-images.githubusercontent.com/74781135/202984967-613bff77-c624-4d03-8b6d-4ad4549b2bb5.png)

Bước 3: Tất cả sản phẩm hiện ra. Bài lab được hoàn thành
![image](https://user-images.githubusercontent.com/74781135/202985153-e54014c7-fa52-4a46-a220-7ff6312f8642.png)

## Subverting application logic
**Lab: SQL injection vulnerability allowing login bypass**

Nhập username là: **administrator'--** và password bất kỳ. Bài lab được hoàn thànhh
![image](https://user-images.githubusercontent.com/74781135/202986022-a3883e49-5b92-4b5b-a588-afaf3e09c50f.png)

## Retrieving data from other database tables
**Lab: SQL injection UNION attack, determining the number of columns returned by the query**

Thay đổi giá trị của parameter category. Thêm **'+UNION+SELECT+null--**
![image](https://user-images.githubusercontent.com/74781135/202988961-a09b2ae4-d409-47d6-b490-6b7a1b777170.png)

Phản hồi báo lỗi

![image](https://user-images.githubusercontent.com/74781135/202989104-c0f488eb-8acc-4b31-bb36-296a09c855ac.png)

Thêm giá trị null đến khi thành công

![image](https://user-images.githubusercontent.com/74781135/202989394-94b91bf0-dfc3-491a-80f5-abb692ed6c55.png)

![image](https://user-images.githubusercontent.com/74781135/202989444-b0a6dfe8-4dbb-4b72-b8c0-4b364785debd.png)

![image](https://user-images.githubusercontent.com/74781135/202989538-ea36c3eb-32c8-49e8-889e-3767c2fff6fb.png)

![image](https://user-images.githubusercontent.com/74781135/202990214-42ecb8a3-5617-4508-b0a4-447c4833b6e2.png)

**Lab: SQL injection UNION attack, finding a column containing text**

Xác định số cột

![image](https://user-images.githubusercontent.com/74781135/202991452-abfadc28-798b-48ca-af2a-229b0eb7ec80.png)

![image](https://user-images.githubusercontent.com/74781135/202991535-8c829c18-e8a7-4bbf-b484-95765e0c3c8a.png)

=> Có 3 cột

Thay từng giá trị null bằng chuỗi bất kỳ để kiểm tra xem cột vào trong truy vấn ban đầu trả về kiểu dữ liệu chuỗi

Thử ở cột đầu tiên. Phản hồi báo lỗi

![image](https://user-images.githubusercontent.com/74781135/202992775-cc344b6b-ec6f-4bed-9768-a4c313591e03.png)

![image](https://user-images.githubusercontent.com/74781135/202992061-9ac5738c-12eb-40ed-a94c-4de8f7f4a13a.png)

Thử ở cột thứ hai. Phản hồi thành công

![image](https://user-images.githubusercontent.com/74781135/202992963-b22b9036-6187-4ee9-b616-66157238666b.png)

![image](https://user-images.githubusercontent.com/74781135/202993029-932a8269-6308-45ec-8bbc-07f2b9ce1e3e.png)

=> Cột 2 của truy vấn ban đầu trả về kiểu dữ liệu chuỗi

**Lab: SQL injection UNION attack, retrieving data from other tables**

Xác định được có 2 cột 

![image](https://user-images.githubusercontent.com/74781135/202994620-f2a17a02-0a27-4504-a4df-b1416c972cd7.png)

![image](https://user-images.githubusercontent.com/74781135/202994656-7a228323-647c-44f0-9cbf-1a7cf589de20.png)

Cả hai cột đều có kiểu dữ liệu chuỗi

![image](https://user-images.githubusercontent.com/74781135/202994883-cf18c454-914e-481b-9012-55e1f8f97b66.png)

![image](https://user-images.githubusercontent.com/74781135/202994960-1c389df7-bd72-4e98-b466-275bdb3b6a4b.png)

![image](https://user-images.githubusercontent.com/74781135/202995226-3a72b4d4-75ec-4b2f-9419-34b450196f6b.png)

![image](https://user-images.githubusercontent.com/74781135/202995360-f66b7972-4240-4f8b-b3df-7630c199ee18.png)

Thay đổi giá trị parameter category để lấy được danh sách username và password

![image](https://user-images.githubusercontent.com/74781135/202995625-73173bf6-cd1d-41b4-b6a8-e9553153b26d.png)

![image](https://user-images.githubusercontent.com/74781135/202995695-d0c531fc-7bf7-4758-aec9-edc79d225eef.png)

Truy cập vào tài khoản administrator và hoàn thành bài lab

![image](https://user-images.githubusercontent.com/74781135/202995958-e6a893af-b7eb-4eb4-99d9-cce8cec63cdf.png)

**Lab: SQL injection UNION attack, retrieving multiple values in a single column**

Xác định được có 2 cột

![image](https://user-images.githubusercontent.com/74781135/202997012-c3da27c0-3961-4551-852c-cbf6cee6d702.png)

Xác định kiểu dữ liệu của 2 cột

Cột 1 không phải kiểu dữ liệu chuỗi

![image](https://user-images.githubusercontent.com/74781135/202998379-d085ca3d-7993-4127-871f-25e67d3883c5.png)

Cột 2 có kiểu dữ liệu là chuỗi

![image](https://user-images.githubusercontent.com/74781135/202998487-fe80eb18-408f-4557-b771-abec824c6e86.png)

Do chỉ có một cột có kiểu dữ liệu chuỗi, nên để lấy được cả username và password, cần nối 2 cột này lại với nhau. Sử dụng toán tử **||** để nối cột username và password thành một cột

Thay giá trị của parameter category để lấy được username và password

![image](https://user-images.githubusercontent.com/74781135/202999105-856ec5e3-808b-4370-912a-582cb1433319.png)

![image](https://user-images.githubusercontent.com/74781135/202999192-56c84ab9-61de-4321-ab8c-889fb5b13b86.png)

Truy cập vào tài khoản administrator và hoàn thành bài lab

![image](https://user-images.githubusercontent.com/74781135/202999329-7fdfe42c-4880-4dee-8ad9-b8b341d8c3c8.png)

## Examining the database
### Querying the database type and version
**Lab: SQL injection attack, querying the database type and version on Oracle** (Có tham khảo solution)

Xác định được có 2 cột và đều là kiểu dữ liệu chuỗi

![image](https://user-images.githubusercontent.com/74781135/203008271-487d665d-6b7a-442f-8dc7-d2d9f7c01f48.png)

![image](https://user-images.githubusercontent.com/74781135/203008368-c59a2a2e-fb19-4e6b-ad91-5fe0da4bee41.png)

Thay giá trị của parameter category để lấy được version 

![image](https://user-images.githubusercontent.com/74781135/203008879-576a19a8-7d07-4f91-819f-7a4394cf74cb.png)

Sử dụng BANNER vì:

![image](https://user-images.githubusercontent.com/74781135/203009236-40f1f140-cf9c-4925-a555-935b4cab29d5.png)

**Lab: SQL injection attack, querying the database type and version on MySQL and Microsoft**

Xác định được có 2 cột và đều là kiểu dữ liệu chuỗi

![image](https://user-images.githubusercontent.com/74781135/203013537-3d2ad0bd-6013-4710-93d9-cf167acaeaba.png)

Thay giá trị của parameter category để lấy được version

![image](https://user-images.githubusercontent.com/74781135/203014496-8a294ce0-2f97-4f00-81f8-091e09b41f0c.png)

![image](https://user-images.githubusercontent.com/74781135/203013831-0642cfbc-e831-4a5c-8477-4a3ad48895b9.png)

### Listing the contents of the database
**SQL injection attack, listing the database contents on non-Oracle databases**

Xác định được có 2 cột và đều là kiểu dữ liệu chuỗi

![image](https://user-images.githubusercontent.com/74781135/203022933-599347f8-7ae2-4ae1-b6a1-5f04930f062e.png)

Liệt kê các schema và các bảng có trong csdl

![image](https://user-images.githubusercontent.com/74781135/203023567-61c57bab-ba05-4400-af23-47d58a25c80a.png)

Trong số các bảng được liệt kê ra có bảng chứa thông tin users

![image](https://user-images.githubusercontent.com/74781135/203023824-b8271a38-6b39-4897-bd6a-6a8c972f147d.png)

Xem trong bảng users_nbmjgq có những cột nào

![image](https://user-images.githubusercontent.com/74781135/203024790-e6f078db-bb94-4353-854e-51cad9c6e933.png)

Liệt kê danh sách username và password

![image](https://user-images.githubusercontent.com/74781135/203025455-504b7f44-ad61-4a0d-b266-08466338d843.png)

Đăng nhập vào administrator và hoàn thành bài lab

![image](https://user-images.githubusercontent.com/74781135/203025684-3a654059-1d8a-4112-bc85-8271503d9166.png)

**SQL injection attack, listing the database contents on Oracle**

**Link tham khảo:**

https://docs.oracle.com/cd/B19306_01/server.102/b14237/statviews_2105.htm#REFRN20286

https://docs.oracle.com/cd/B19306_01/server.102/b14237/statviews_2094.htm

Xác định được có 2 cột và đều là kiểu dữ liệu chuỗi

![image](https://user-images.githubusercontent.com/74781135/203026411-9ead4853-800e-4296-b218-5c680b18016b.png)

Liệt kê danh sách các bảng trong cơ sở dữ liệu

![image](https://user-images.githubusercontent.com/74781135/203026818-323d72c4-6b7a-4976-b5f0-69b68f034141.png)

![image](https://user-images.githubusercontent.com/74781135/203026932-a0e06d38-2523-4312-bded-da9b2d15fd19.png)

Trong số các bảng vừa liệt kê có bảng chứa thông tin users

![image](https://user-images.githubusercontent.com/74781135/203027243-7b66dcb3-a2ef-495d-974d-fcc9430857c4.png)

Xem trong bảng USERS_UEUXPI có những cột nào

![image](https://user-images.githubusercontent.com/74781135/203028059-8a0f61d3-f412-438e-aabd-e1e91339f88c.png)

![image](https://user-images.githubusercontent.com/74781135/203028114-c5ce4443-347c-4f9b-8833-b46024f66df2.png)

Liệt kê danh sách username và password

![image](https://user-images.githubusercontent.com/74781135/203028514-2c13553b-7c84-4b16-b4df-279e8d8c735e.png)

![image](https://user-images.githubusercontent.com/74781135/203028602-9cc01409-8a8c-49af-b6c4-5ca2ab5fc9e9.png)

Đăng nhập vào administrator để hoàn thành bài lab

![image](https://user-images.githubusercontent.com/74781135/203028795-4e071c23-8c61-4db1-bd63-f5d99c59abb8.png)


