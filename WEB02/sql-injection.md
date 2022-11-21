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


