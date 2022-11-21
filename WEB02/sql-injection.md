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

## Blind SQL injection
**Lab: Blind SQL injection with conditional responses** (Có tham khảo solution)

Bước 1: Bắt request có chứa TrackingId và gửi đến Repeater

![image](https://user-images.githubusercontent.com/74781135/203067658-414fe084-a6f2-4b29-9da7-6d91c355a4ed.png)

Bước 2: Thay đổi TrackingId. Xuất hiện thông báo Welcome back

![image](https://user-images.githubusercontent.com/74781135/203068139-83ffffab-230e-40f9-b037-4fc18324130f.png)

Bước 3: Thay đổi TrackingId. Không xuất hiện thông báo Welcome back

![image](https://user-images.githubusercontent.com/74781135/203068887-280510e6-ec43-4e57-9c98-dc5b337bb755.png)

Bước 4: Thay đổi TrackingId=gJGmqPiif2kli2R7' AND (SELECT 'a' FROM users LIMIT 1)='a. Có xuất hiện thông báo Welcome back => có bảng users

![image](https://user-images.githubusercontent.com/74781135/203069533-fee9d7b1-f48c-4e2d-ad70-8f8ad69a1fa5.png)

Bước 5: Thay đổi TrackingId=gJGmqPiif2kli2R7' AND (SELECT 'a' FROM users WHERE username='administrator')='a. Có xuất hiện thông báo Welcom back => có users administrator

![image](https://user-images.githubusercontent.com/74781135/203070193-9a0516bd-4115-4345-b7c7-641fc9892f73.png)

Bước 6: Xác định xem có bao nhiêu ký tự trong mật khẩu của administrator

![image](https://user-images.githubusercontent.com/74781135/203070841-b5227e8a-dba3-41c1-a45d-d8472e919610.png)

=> Mật khẩu có độ dài lớn hơn 1

Bước 7: Sử dụng Intruder để xác định chính xác số ký tự trong mật khẩu của administrator

![image](https://user-images.githubusercontent.com/74781135/203071562-79c9fd12-afd7-4dc4-96a4-f6019e264911.png)

![image](https://user-images.githubusercontent.com/74781135/203071830-b851627f-c41b-42bc-8822-26a00c91362a.png)

![image](https://user-images.githubusercontent.com/74781135/203071967-20aceb64-5a76-430e-9b4c-15455c8c40d7.png)

![image](https://user-images.githubusercontent.com/74781135/203072263-52736681-eb27-4d5b-a906-e9f5ae567890.png)

=> Password có 20 ký tự

Bước 8: Kiểm tra ký tự ở từng vị trí để xác định giá trị của nó

![image](https://user-images.githubusercontent.com/74781135/203073450-32fb00f9-c7ee-495e-a0ca-111c963af3d6.png)

![image](https://user-images.githubusercontent.com/74781135/203073687-c0bb3d44-a942-415d-8498-c9427785a30e.png)

![image](https://user-images.githubusercontent.com/74781135/203073725-5f49c86b-d080-41e4-8c81-15bee09ea911.png)

![image](https://user-images.githubusercontent.com/74781135/203073959-52571f43-3144-4c60-9db3-cbcb0b38bb14.png)

=> Ký tự đầu tiên của mật khẩu là '7'

Bước 9: Làm tương tự đến khi lấy được toàn bộ mật khẩu là: **7uzje0sv01nqbe10yr2w**

Bước 10: Đăng nhập vào tài khoản administrator để hoàn thành bài lab
![image](https://user-images.githubusercontent.com/74781135/203076087-f9d29f7a-3ee3-45ef-a700-9b0acd585478.png)

**Lab: Blind SQL injection with conditional errors**

### Exploiting blind SQL injection by triggering time delays
**Lab: Blind SQL injection with time delays**

Bước 1: Bắt request có chứa TrackingId

![image](https://user-images.githubusercontent.com/74781135/203087852-0e81bb7c-f0e1-49da-b12a-8fd7bc857b27.png)

Bước 2: Thay đổi TrackingId=UPwCcYVrM8xRDKTX'||pg_sleep(10)--

![image](https://user-images.githubusercontent.com/74781135/203087956-e125b86c-b4cd-4fe7-aa6f-0d97eb05bc02.png)

Bài lab được hoàn thành

![image](https://user-images.githubusercontent.com/74781135/203088372-f90bedff-eda8-41b4-a716-64c47a2cc299.png)

**Lab: Blind SQL injection with time delays and information retrieval** (Có tham khảo solution)

Bước 1: Bắt request có chứa TrackingId và gửi đến Repeater

![image](https://user-images.githubusercontent.com/74781135/203092517-dda7ffad-647d-4c51-b5a3-c10a0ee43eb4.png)

Bước 2: Thay đổi TrackingId=EIevL183HZTXPvQ8'%3BSELECT+CASE+WHEN+(1=1)+THEN+pg_sleep(10)+ELSE+pg_sleep(0)+END--

Mất 10s để phản hồi

Bước 3: Thay đổi TrackingId=EIevL183HZTXPvQ8'%3BSELECT+CASE+WHEN+(usernam='administrator')+THEN+pg_sleep(10)+ELSE+pg_sleep(0)+END+FROM+users--

Vẫn mất 10s để phản hổi chứng tỏ có tồn tại username administrator trong bảng users

Bước 4: Xác định xem có bao nhiêu ký tự trong mật khẩu

![image](https://user-images.githubusercontent.com/74781135/203095429-67a56495-3384-4904-ad33-56647f94f0d6.png)

Bước 5: Gửi request đến Intruder để tìm mật khẩu chính xác. Thêm payloads, chọn kiểu tấn công là Cluster Bomb

![image](https://user-images.githubusercontent.com/74781135/203096223-566c6213-b7a2-44ec-9d00-333b7a39f545.png)

![image](https://user-images.githubusercontent.com/74781135/203096461-f213012c-0f91-41e3-a390-bfafabc8056f.png)

![image](https://user-images.githubusercontent.com/74781135/203096643-69a5f3f9-2044-4ffb-a0ba-84ae22a7996d.png)

Bước 6: Sau khi quét xong thu được mật khẩu là: 

**Lab: Blind SQL injection with out-of-band interaction** (Có tham khảo solution)

Bước 1: Bắt request có chứa TrackingId và gửi đến Repeater

![image](https://user-images.githubusercontent.com/74781135/203101251-10c6f9a9-88c8-4258-9a07-12ee9e431fde.png)

Bước 2: Thay đổi giá trị TrackingId

![image](https://user-images.githubusercontent.com/74781135/203101801-2f45281e-fa28-4695-8960-0fedc30e96b2.png)

Bước 3: Mở Burp Collaborator client. Copy đường dẫn: 143dxs61pfejum5lhc5olqnl4ca3yumj.oastify.com và paste lại vào TrackingId

![image](https://user-images.githubusercontent.com/74781135/203103686-ac38a9ba-5941-4cbb-bd01-375592001c8a.png)

Bài lab được hoàn thành

![image](https://user-images.githubusercontent.com/74781135/203103799-3572436e-531b-4221-940b-5c90e60e3802.png)

**Lab: Blind SQL injection with out-of-band data exfiltration** (Có tham khảo solution)

Bước 1: Bắt request có chứa TrackingId và gửi đến Repeater

![image](https://user-images.githubusercontent.com/74781135/203104487-4934c7e8-b047-453f-84a7-c8853eccee10.png)

Bước 2: Bật Burp Collaborator client, copy đường dẫn. Sau đó thay đổi giá trị của TrackingId. Gửi request

![image](https://user-images.githubusercontent.com/74781135/203105064-a2aef216-f889-4011-aa1b-b703d4333d39.png)

Bước 3: Vào Burp Collaborator client, chọn Poll now. Click vào một dòng bất kỳ. Password chính là subdomain

![image](https://user-images.githubusercontent.com/74781135/203110348-8d271f82-93e5-4d3c-aa51-fb4297382d7f.png)

Bước 4: Đăng nhập vào administrator để hoàn thành bài lab

![image](https://user-images.githubusercontent.com/74781135/203110566-9ea2ff5c-e241-465c-bb17-7e639906b09c.png)
