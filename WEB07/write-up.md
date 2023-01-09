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
### Exploiting DOM XSS with different sources and sinks
**Lab: DOM XSS in `document.write` sink using source `location.search`**

Bước 1: Tìm kiếm với một từ bất kỳ. Giá trị tìm kiếm được nối vào thuộc tính `src` của thẻ `img`

![image](https://user-images.githubusercontent.com/74781135/210920003-9f23d3e6-bbd5-4352-9b02-861ba0104f6f.png)

![image](https://user-images.githubusercontent.com/74781135/210920043-c5ae768f-6550-4fbb-ae4e-0e4435a4c236.png)

Bước 2: Đóng thẻ `img` sau đó thực thi đoạn script bằng cách nhập tìm kiếm là: `"><script>alert("DOM XSS")</script>`

![image](https://user-images.githubusercontent.com/74781135/210920621-c97bc070-93c8-487b-99ff-27e76433f7e0.png)

Bài lab được hoàn thành

![image](https://user-images.githubusercontent.com/74781135/210920659-29ad525e-3758-4499-b107-080b16e91cf7.png)

**Lab: DOM XSS in `document.write` sink using source `location.search` inside a select element**

Bước 1: Truy cập vào một sản phẩm bất kỳ. Đoạn script thực thi

![image](https://user-images.githubusercontent.com/74781135/210951057-8a693b2b-96d9-4f40-b1fb-3d77612ba32a.png)

Có thể thấy đoạn js lấy `stotrId` từ `location.search` sau đó sử dụng `document.write` để tạo một tùy chọn mới cho chức năng kiểm tra số lượng sản phẩm trong kho

Bước 2: Thêm tham số storeId với giá trị bất kỳ vào URL và gửi đi

![image](https://user-images.githubusercontent.com/74781135/210952044-458f6a21-f8dc-4b16-a467-7e626d2e747a.png)

Giá trị của storeId là `Vietnam` đã được thêm mới vào trong thẻ select

![image](https://user-images.githubusercontent.com/74781135/210952429-36073e2c-0f24-4dec-8d66-37a200cc4726.png)

Bước 3: Tìm kiếm với giá trị khác của tham số storeId sao cho kết thúc thẻ select và thực thi đoạn script độc hại: `"></select><script>alert(1)</script>`

![image](https://user-images.githubusercontent.com/74781135/210953132-83ef796d-2044-4000-b755-caf30704c122.png)

Bài lab được hoàn thành

![image](https://user-images.githubusercontent.com/74781135/210953229-edc7794d-e213-4111-abd5-b34cdb78a26b.png)

**Lab: DOM XSS in `innerHTML` sink using source `location.search`**

Bước 1: Tìm kiếm với một từ bất kỳ

![image](https://user-images.githubusercontent.com/74781135/210955657-2bce7496-d26a-44a7-b00c-fb3be604a0f5.png)

 Đoạn script thực thi

![image](https://user-images.githubusercontent.com/74781135/210955099-3007ff93-7439-4964-a7a2-18a4294e0327.png)

Có thể thấy đoạn code js lấy giá trị tham số search từ location.search sau đó sử dụng `innerHHTML` để set nội dung trong thẻ `span` có id="searchMessage"

![image](https://user-images.githubusercontent.com/74781135/210955619-fd7872d4-471e-433d-8868-195ba6baf2c6.png)

Bước 2: Tìm kiếm với từ khóa `</span><<img src=1 onerror=alert("XSS")>`

![image](https://user-images.githubusercontent.com/74781135/210956077-a9961162-846a-4638-94ab-36f0bf4ea874.png)

Bài lab được hoàn thành

![image](https://user-images.githubusercontent.com/74781135/210956153-16932173-4e70-45e7-a2d0-74c36edcc8e1.png)

### Sources and sinks in third-party dependencies
#### DOM XSS in jQuery
**Lab: DOM XSS in jQuery anchor `href` attribute sink using `location.search` source**

Bước 1: Vào tính năng submit feedback của trang web. Chức năng Back có một đoạn js thực thi

![image](https://user-images.githubusercontent.com/74781135/210966971-934d6d13-5d78-493d-96fa-6875e4023e88.png)

Có thể thấy, đoạn code cho phép thay đổi giá trị thuộc tính `href` của thẻ `a` bằng cách sử dụng hàm `attr()` của Jquery

Thử thay URL thành: `returnPath=minh` 

Giá trị của thuộc tính `href` đã thay đổi

![image](https://user-images.githubusercontent.com/74781135/210967411-9fd56d44-0db8-4530-8bbb-64b5665d4000.png)

Thay đổi URL thành: `return=javascript:alert(document.cookie)`

![image](https://user-images.githubusercontent.com/74781135/210967664-b7dbad13-458f-4081-94a1-daed614c063c.png)

Bài lab được hoàn thành

![image](https://user-images.githubusercontent.com/74781135/210967760-e0c7b20f-1e7f-4baf-8a9d-f95a704182d0.png)

**Lab: DOM XSS in jQuery selector sink using a hashchange event**

Bước 1: Truy cập vào trang web. Đoạn script thực thi

![image](https://user-images.githubusercontent.com/74781135/211229502-6397740d-1620-4649-859a-ea56cd54a2e6.png)

Bước 2: Vào exploit server, sửa phần body thành

![image](https://user-images.githubusercontent.com/74781135/211230287-2fc36ea9-ee2a-4098-94ee-8415910eef97.png)

Bước 3: Chọn `Store` sau đó chọn `Deliver exploit to victim`. Bài lab được hoàn thành

![image](https://user-images.githubusercontent.com/74781135/211230408-c182b25f-5538-4736-9e44-4bd05ae51c8e.png)

#### DOM XSS in AngularJS
### DOM XSS combined with reflected and stored data
