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
