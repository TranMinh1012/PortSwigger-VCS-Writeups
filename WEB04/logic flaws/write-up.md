# Logic Flaws (Business Logic)
## Excessive trust in client-side controls
**Lab 1: Excessive trust in client-side controls**

Bước 1: Đăng nhập vào tài khoản được cung cấp, tài khoản có 100$ để mua hàng

![image](https://user-images.githubusercontent.com/74781135/205191942-4020c846-46de-4848-94d1-85c97ce97163.png)

Bước 2: Thêm sản phẩm **Lightweight l33t leather jacket** vào giỏ hàng, bắt request và thay đổi giá tiền của sản phẩm

![image](https://user-images.githubusercontent.com/74781135/205192329-93ba8f14-74c2-438c-8e7c-a0fb41c5be29.png)

![image](https://user-images.githubusercontent.com/74781135/205192381-7fa95244-7225-46c5-8498-b5c745281946.png)

Bước 3: Click Place order để mua sản phẩm và hoàn thành bài lab

![image](https://user-images.githubusercontent.com/74781135/205192456-7f75c14a-4afd-4dba-9f3e-134648231d21.png)

## Failing to handle unconventional input
**Lab 2: High-level logic vulnerability**

Bước 1: Đăng nhập vào tài khoản được cung cấp, tài khoản có 100$ để mua hàng

![image](https://user-images.githubusercontent.com/74781135/205189964-50a2c274-ebb6-4e3b-96ba-a027a91b75b8.png)

Bước 2: Thêm sản phẩm **Lightweight l33t leather jacket** vào giỏ hàng

![image](https://user-images.githubusercontent.com/74781135/205190459-8358965d-4441-418d-86a5-22c688f999c8.png)

Bước 3: Thay đổi số lượng sản phẩm, bắt request này và đổi số lượng thành `-2`

![image](https://user-images.githubusercontent.com/74781135/205190699-08f66a1b-7a6c-4c25-9e75-c34de6cb2eac.png)

![image](https://user-images.githubusercontent.com/74781135/205190765-d6246e65-3585-4540-9204-3f932cca5def.png)

Bước 4: Thử Place order thì nhận được thông báo tổng tiền không được nhỏ hơn 0

![image](https://user-images.githubusercontent.com/74781135/205190914-6fcbb2ec-33a2-4b12-8af2-0548adcdc03b.png)

Có thể nhận thấy mua được sản phẩm với số lượng âm nếu thỏa mãn điều kiện tổng tiền không âm

Bước 5: Thêm một sản phẩm khác vào giỏ hàng, thay đổi số lượng của sản phẩm đó đến khi tổng tiền là hợp lệ

![image](https://user-images.githubusercontent.com/74781135/205191705-34d8cb2b-f1b2-47bb-a242-60d0d6d39a00.png)

Bước 6: Click Place order để hoàn thành bài lab

![image](https://user-images.githubusercontent.com/74781135/205191789-f78d3f85-e579-4b90-a514-367bb3878fd9.png)

**Lab 5: Low-level logic flaw**

Bước 1: Đăng nhập vào tài khoản được cung cấp

Bước 2: Thêm sản phẩm **Lightweight l33t leather jacket** vào giỏ hàng

Không thể mua sản phẩm với số lượng âm giống như bài lab trước đó, ta có thể thử trường hợp cố gắng tạo ra một mức giá cao vượt trội. Giá được lưu trữ trong một số loại biến số. Khi nó vượt quá giá trị tối đa, nó thường tràn đến giá trị thấp nhất có thể và tiếp tục đếm từ đó:

![image](https://user-images.githubusercontent.com/74781135/205201301-fb19c947-f880-41d5-a784-46410377fb2d.png)

Bước 3: Thay đổi số lượng sản phẩm, bắt request và gửi đến Burp Intruder

Bước 4: Đặt payload ở quantity và tiến hành attack

![image](https://user-images.githubusercontent.com/74781135/205201745-3843fd68-f0e7-4f16-9b68-9dbef6bae9dd.png)

Bước 5: Khi đạt đến một ngưỡng nhất định ta sẽ thấy tổng giá tiền bị âm

![image](https://user-images.githubusercontent.com/74781135/205201848-bc3838c7-f326-4c1c-9ab1-2e6ddf13fb87.png)

Bước 6: Tăng số lượng sản phẩm, bắt request và sửa số lượng thành **12762** và gửi request

![image](https://user-images.githubusercontent.com/74781135/205204084-a38102ae-b151-427d-8038-f4175342bde1.png)

Khi này tổng tiền sẽ là: 

![image](https://user-images.githubusercontent.com/74781135/205204299-033a80aa-6e10-4f66-813a-f1abea3fbc11.png)

Bước 7: Thêm một sản phẩm bất kỳ vào giỏ hàng và điều chỉnh số lượng để tổng giá nằm trong khoảng 0 đến 100

![image](https://user-images.githubusercontent.com/74781135/205204506-8110bd27-2de2-4227-b57f-29e376724182.png)

Bước 8: Click Place order mua sản phẩm và hoàn thành bài lab

![image](https://user-images.githubusercontent.com/74781135/205204609-97c3979c-3ab6-472e-8fab-d1abb63e50c5.png)

**Lab 6: Inconsistent handling of exceptional input**

## Users won't always follow the intended sequence
**Lab 8: Insufficient workflow validation**

Bước 1: Đăng nhập vào tài khoản được cung cấp 

Bước 2: Thêm sản phẩm **Lightweight l33t leather jacket** vào giỏ hàng

Bước 3: Click Place order và xem request

![image](https://user-images.githubusercontent.com/74781135/205538993-a0622d2b-2a6a-4369-9d72-591f8f83c039.png)

Việc thanh toán sẽ trả ra `303 See Other`. Điểm đặc biệt là ở **Location** chứa đường dẫn thông báo lỗi.

Bước 4: Thử mua một sản phẩm có thể mua

![image](https://user-images.githubusercontent.com/74781135/205540102-992ff0ec-8db9-41a7-96b7-11f9c9da47b6.png)

Chuyển hướng đi đến một trang khác với xác nhận đơn hàng.

Bước 5: Mua lại sản phẩm **Lightweight l33t leather jacket**, chặn request và thay đổi chuyển hướng

![image](https://user-images.githubusercontent.com/74781135/205540596-82bc2bbf-cf04-4a13-a9d8-56e4a5f99ee3.png)

![image](https://user-images.githubusercontent.com/74781135/205540681-5666f9b6-5d6b-4318-ad38-2249afdb4fb1.png)

**Lab 9: Authentication bypass via flawed state machine**

Bước 1: Đăng nhập vào tài khoản được cung cấp

Bước 2: Chọn role là User và xem request

![image](https://user-images.githubusercontent.com/74781135/205542262-486ff493-26f2-4bb5-8c41-bf4edc91070f.png)

Bước 3: Thử thay đổi role thành `admin` và `administrator` nhưng không có gì đặc biệt xảy ra

Thử Drop request chọn role

Bước 4: Đăng nhập lại vào tài khoàn `wiener:peter`, chăn request và drop request chọn role. Quay lại trang My account thì thấy đã login vào tài khoản quản trị viên

![image](https://user-images.githubusercontent.com/74781135/205543802-1c452a73-c8b4-442b-88ce-f62a6154be00.png)

Bước 5: Xóa Carlos để hoàn thành bài lab

![image](https://user-images.githubusercontent.com/74781135/205543858-f00be100-0905-4fb7-984a-d292812baec2.png)

## Trusted users won't always remain trustworthy
**Lab 3: Inconsistent security controls**

Bước 1: Đăng ký tài khoản với email được cung cấp

![image](https://user-images.githubusercontent.com/74781135/205526608-584dc6e6-8951-4e93-90bc-20970b13f695.png)

Bước 2: Xác nhận email để đăng nhập vào tài khoản

![image](https://user-images.githubusercontent.com/74781135/205526749-b726bcf8-8c85-4dbb-8d69-896140063e11.png)

Bước 3: Thay đổi email 

![image](https://user-images.githubusercontent.com/74781135/205526863-1513aef0-3704-45db-adfa-6bf601620d2d.png)

Sau khi thay đổi email, thấy xuất hiện Admin panel

![image](https://user-images.githubusercontent.com/74781135/205526983-6da16634-cb6b-41a7-a518-59b67a7a27c4.png)

Bước 4: Truy cập vào Admin panel, xóa Carlos để hoàn thành bài lab

![image](https://user-images.githubusercontent.com/74781135/205527080-6f862c89-db00-4c87-8d16-84ee976f1144.png)

## Users won't always supply mandatory input
**Lab 7: Weak isolation on dual-use endpoint**

Bước 1: Đăng nhập vào tài khoản được cung cấp

Bước 2: Thử đổi username = administrator và thay đổi mật khẩu

![image](https://user-images.githubusercontent.com/74781135/205545026-551dd4af-8c79-490d-bbd0-84b046922079.png)

Có thể thấy việc so sánh mật khẩu không được thực hiện với tài khoản mật khẩu đã đăng nhập mà được thực hiện với mật khẩu của người dùng trong trường Username.

![image](https://user-images.githubusercontent.com/74781135/205546524-8eb76969-b241-4ede-86b0-5073a1940224.png)

Trong khi ứng dụng tạo ra phản hồi thì người dùng là administrator và người dùng là administrator khi mật khẩu hiện tại được kiểm tra nên mới có thông báo lỗi

Bước 4: Thử xóa mật khẩu hiện tại

![image](https://user-images.githubusercontent.com/74781135/205547135-10a99aa9-9855-4c6e-b7aa-6259db17985b.png)

Bước 5: Thử đăng nhập tài khoản administrator với password vừa đặt 

![image](https://user-images.githubusercontent.com/74781135/205547460-2c6af365-9bee-4faf-ac10-970e0abf2c8f.png)

Bước 6: Xóa carlos để hoàn thành bài lab

![image](https://user-images.githubusercontent.com/74781135/205547563-336e7d03-d3bd-4b85-a54a-87e90e20f7bb.png)

## Domain-specific flaws
**Lab 4: Flawed enforcement of business rules**

Bước 1: Đăng nhập và tài khoản được cung cấp

Bước 2: Thêm sản phẩm **Lightweight l33t leather jacket** vào giỏ hàng

Bước 3: Áp dụng mã giảm giá thì được giảm 5$

![image](https://user-images.githubusercontent.com/74781135/205535545-6f2ed1eb-9925-495b-8f25-a31433a110d4.png)

Thử áp dụng mã giảm giá lần nữa thì thông báo lỗi

![image](https://user-images.githubusercontent.com/74781135/205535681-92e7c6bc-cb71-4787-aa45-ac280f989269.png)

Bước 4: Đăng ký để nhận mã giảm giá khác ở cuối trang

![image](https://user-images.githubusercontent.com/74781135/205535929-7b4e6baf-2476-4013-9158-572c850060a6.png)

Nhận được mã giảm giá khác

![image](https://user-images.githubusercontent.com/74781135/205536037-c79c3be9-2e10-4aa9-b7c3-db492905cbca.png)

Bước 5: Áp dụng mã giảm giá mới

![image](https://user-images.githubusercontent.com/74781135/205536245-16e43fa0-834d-4f10-bf82-ca6f107586a6.png)

Bước 6: Thử sử dụng lại mã giảm giá cũ ta thấy mã giảm giá vẫn được áp dụng

![image](https://user-images.githubusercontent.com/74781135/205536414-adbaa7b8-b2e7-4c85-a24c-55e6d70e1455.png)

Có vẻ như kiểm tra chỉ được thực hiện với mã giảm giá mới nhất được áp dụng.

Bước 7: Sử dụng sen kẽ các mã giảm giá đến khi muc được hàng

![image](https://user-images.githubusercontent.com/74781135/205536690-a36f1c94-0872-431e-9fd4-c546cb6f8a55.png)

Bước 8: Chọn Place order để mua sản phẩm và hoàn thành bài lab

![image](https://user-images.githubusercontent.com/74781135/205536794-a6487fc9-e9ff-4667-a442-0ce3effd7eee.png)
