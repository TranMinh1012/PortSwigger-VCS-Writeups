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

## SSRF attacks against other back-end systems
**Lab 2: Basic SSRF against another back-end system**

Bước 1: Truy cập vào một sản phẩm bất kỳ và kiểm tra xem sản phẩm ý còn bao nhiêu trong kho

Bước 2: Chặn bắt request POST kiểm tra số lượng sản phẩm trong kho. Thay đổi URL, gửi đến Intruder và đặt payload

![image](https://user-images.githubusercontent.com/74781135/209146805-84a99a7b-46da-42ff-bb65-a9e16b92c6b9.png)

![image](https://user-images.githubusercontent.com/74781135/209145976-2fc35020-73ac-469b-a1a7-2048f8138c90.png)

Bước 3: Tiến hành tấn công

![image](https://user-images.githubusercontent.com/74781135/209147078-9c98fc94-65d3-4a56-9ca5-00b48cff7b9b.png)

Kết quả hiển thị một phản hồi 200 OK duy nhất, đó là IP của giao diện quản trị.

Bước 4: Request đến địa chỉ IP

![image](https://user-images.githubusercontent.com/74781135/209147606-8e3f1e57-e1f3-456d-9f79-15f215f75392.png)

Bước 5: Copy link để xóa người dùng carlos

![image](https://user-images.githubusercontent.com/74781135/209147820-c08cba17-78c5-460a-b77e-ee3f61218d34.png)

![image](https://user-images.githubusercontent.com/74781135/209147896-054f8ef7-90ad-4246-bf46-b8ff0ad5e1ed.png)

## SSRF with blacklist-based input filters
**Lab 3: SSRF with blacklist-based input filter**

Bước 1: Truy cập vào một sản phẩm bất kỳ và kiểm tra xem sản phẩm ý còn bao nhiêu trong kho

Bước 2: Bắt request, gửi đến Repeater và thay đổi URL

![image](https://user-images.githubusercontent.com/74781135/209152863-f6c71177-8529-4668-9241-28be6f0cff36.png)

Có thể thấy ứng dụng đã chặn đầu vào chứa tên máy chủ là `localhost`

Thử với `127.0.1/admin`

![image](https://user-images.githubusercontent.com/74781135/209153307-e99cda3d-da30-4047-bfab-ec5802998206.png)

Thử với `127.0.1/Admin`

![image](https://user-images.githubusercontent.com/74781135/209153523-ad5d62c6-019f-4bab-bfdc-5442a2050cea.png)

Đã truy cập thành công vào giao diện quản trị

Bước 3: Copy đường link để xóa username carlos

![image](https://user-images.githubusercontent.com/74781135/209153801-6f2ac5a2-8186-4af1-9f18-7750974751e4.png)

![image](https://user-images.githubusercontent.com/74781135/209153844-f9d2afa0-7c74-44b0-b13d-41f5cdda9193.png)

## Bypassing SSRF filters via open redirection
**Lab 4: SSRF with filter bypass via open redirection vulnerability**

Bước 1: Truy cập vào một sản phẩm bất kỳ và kiểm tra xem sản phẩm ý còn bao nhiêu trong kho

Bước 2: Bắt request, gửi đến Repeater và thay đổi URL

![image](https://user-images.githubusercontent.com/74781135/209159943-00458a88-a3a2-48b8-aeaf-2742ec6c6cd9.png)

Có thể thấy không thể yêu cầu trực tiếp được đến máy chủ

Bước 3: Chọn chức năng `Next product`

![image](https://user-images.githubusercontent.com/74781135/209160775-2de8d031-9483-460d-bc9f-706b2656b1e8.png)

Link này chứa một đường dẫn dưới dạng đối số URL và chuyển hướng 302 đến đường dẫn đó

Bước 4: Thử thay đổi liên kết đến một trang bất kỳ

![image](https://user-images.githubusercontent.com/74781135/209161293-5891eea3-b06c-434d-9175-9a05adb99785.png)

-> chuyển hướng mở, sử dụng bất kỳ URL nào được cung cấp làm vị trí chuyển hướng

Bước 5: Thay đổi URL trong request POST kiểm tra số lượng hàng trong kho

![image](https://user-images.githubusercontent.com/74781135/209162530-1884ba3b-9e0f-4430-8313-27a4999dd8e0.png)

Bước 6: Copy đường link để xóa username carlos

![image](https://user-images.githubusercontent.com/74781135/209162932-2bb99046-5883-401f-914e-fa718111d673.png)

![image](https://user-images.githubusercontent.com/74781135/209162972-516af7e9-6bef-4353-91fc-ee0cff6a2084.png)

## Blind SSRF vulnerabilities
**Lab 5: Blind SSRF with out-of-band detection**

Bước 1: Truy cập vào một sản phẩm bất kỳ

![image](https://user-images.githubusercontent.com/74781135/209165117-d9c0382b-9fca-41de-a959-70edd4438b2a.png)

Tất cả các request đều chứa Referer header cho biết trang chứa liên kết được sử dụng. 

Bước 2: Thay đổi Referer header thành URL của Burp Collaborator 

![image](https://user-images.githubusercontent.com/74781135/209166293-cef03a8d-418e-4f99-8bc6-a00690ee0cd8.png)

Bước 3: Gửi request. Sau khi gửi yêu cầu này, Burp Collaborator hiển thị lưu lượng truy cập DNS và HTTP, xác nhận rằng máy chủ đã được dụ dỗ để liên hệ với miền bên ngoài được cung cấp

![image](https://user-images.githubusercontent.com/74781135/209166689-ecf0499f-c250-4a84-b4e4-68979f962100.png)

![image](https://user-images.githubusercontent.com/74781135/209166885-faacb06e-c64e-4085-8d68-2369e3502195.png)
