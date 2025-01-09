# Trang web tài liệu chính thức
Các bạn có thể xem chi tiết ở trang web tại liệu chính thức của FE [Craftland Create Official](https://createofficial.garena.com/vn/docs)


# Các câu hỏi thường gặp

## Người chơi
### 1. Cách để ngụy trang người chơi thành một vật nào đó?
- Bước 1: Tải module **Biến hình (Morph)** trong quản lý Module
- Bước 2: **Dùng lệnh Người chơi biến thành một vật thể trong cảnh (Morph To)** để biến hình ngụy trang.

![image](https://github.com/user-attachments/assets/7dcf91ae-11ef-427c-9088-1ba62f251871)


## Giao diện
### 1. Cách để tắt một giao diện tùy chỉnh (Custom HUD)?
- Cách 1: Gán thuộc tính **Có thể nhìn thấy (IsVisible)** của thực thể giao diện là **FALSE**. Thuộc tính này có thể gán là **TRUE** để hiển thị lại giao diện.
  
  ![image](https://github.com/user-attachments/assets/94c2fa83-2bc7-4798-b3a4-0f2700708d91)

- Cách 2:  Dùng lệnh **Tiêu diệt (Destroy)** để xóa giao diện tùy chỉnh.
  
![image](https://github.com/user-attachments/assets/eb6facad-7204-4953-8cfa-6e95a68b8a14)


### 2. Không hiển thị giao diện kết quả trận đấu sau khi kết thúc trận trên PC Editor?
- Giao diện kết quả trận đấu chỉ có thể xem được khi chơi trên bản đã được xuất bản.
  

## Vũ khí
### 1. Cách để thay đổi các thuộc tính của súng như tốc độ thay đạn, số lượng băng đạn,... là gì?
- Có thể thay đổi các chỉ số của súng bằng cách gán lại giá trị cho các thuộc tính của thực thể vũ khí.

  ![image](https://github.com/user-attachments/assets/938c4cd7-7315-4498-b4f3-7249e60a1c9a)

- Chi tiết các lệnh liên quan đến vũ khí có thể xem thêm [TẠI ĐÂY](https://createofficial.garena.com/vn/docs/component-79)


## Chiến đấu
### 1. Cách để in ra lượng sát thương/kill của 1 người chơi?
- Có thể dùng sự kiện Khi gây DMG (On Deal Damage) để lấy chỉ số sát thương.

![image](https://github.com/user-attachments/assets/1eb0f5b2-17e7-43bb-b720-e76c17c0aa54)


## Thiết kế bản đồ
### 1. Có cách nào để 2 người cùng build một map trên FE không?
- Hiện tại FE chưa hỗ trợ cụ thể tính năng này. Các bạn có thể chia sẻ dự án hoặc map thông qua việc gửi file.
- Chi tiết xem thêm [TẠI ĐÂY](https://github.com/trivyGameCTV/Craftland-Tutorial/blob/main/Ti%E1%BA%BFng%20Vi%E1%BB%87t/40.%20Chia%20s%E1%BA%BB%20d%E1%BB%B1%20%C3%A1n/Chia%20s%E1%BA%BB%20D%E1%BB%B1%20%C3%A1n.md)


### 2.  Cách để chơi thử bản đồ của mình với nhiều người chơi trên PC Editor? 
- Có thể thực hiện bằng cách test map bằng nhiều máy khách trên PC Editor.

![image](https://github.com/user-attachments/assets/cba54564-836a-4002-a15a-be870f17bca5)


### 3. Cách để chỉnh trời ngày đêm trong map?
- Bước 1: Chọn nền trời ở cây phân cấp, nơi hiển thị tất cả các vật thể hiện đang có ở bản đồ.
- Bước 2: Tùy chỉnh các thuộc tính của Nền trời (Skybox) để thay đổi màu trời, ngày, đêm,...

## Model 3D
### 1. Cách import model 3D bên ngoài vào FE?
- Kéo thả file .fbx vào thư mục Assets trong FE để import model 3D. 

## Khác
### 1. Sự kiện tùy chỉnh là gì? Cách sử dụng sự kiện tùy chỉnh?
- Thường các game online sẽ được phân ra thành "client" (máy khách vd: Điện thoại) và "server" (máy chủ)
- Trong một trận đấu, khi người chơi thực hiện bất cứ hành động gì thì để có một lệnh được gửi từ client đến server, server sẽ ghi nhận hành động đó và thực gửi thông tin mới đến tất cả client, thay đổi trận đấu trong thời gian đó.
 
- Khi một sự kiên được gửi , hệ thống sẽ tìm tất cả các vật thể liên quan để gửi sự kiện đó đến. 

- Nếu sự kiện chỉ được gửi cho server, thì những tệp không phải là "Client Script/Client Block Script" sẽ nhận được. 
-> Sẽ tối ưu được performance. 

- Nếu sự kiện chỉ được gửi cho client, thì chỉ những tệp là "Client Script/ Client Block Scipt" sẽ nhận được. 
-> Sẽ tối ưu được performance. 

- Chọn "Local" thì nếu sự kiện được gửi ở client thì chỉ client nhận được, còn nếu gửi ở server thì chỉ ở server nhận được 
-> Sẽ tối ưu được performance. 

- Chọn "Both" thì cả client và server đều nhận được. 
-> Nặng hơn về performance 


### 2. Key là gì? Cách sử dụng key?
- Trong thư mục localization có một file là key.csv
- Được dùng để hệ thống tự động thay đổi ngôn ngữ tùy vào setting của người dùng. 
- Chỉ cần điền tất cả các cột và sử dụng key ở những nơi có text hiển thị thì hệ thống sẽ tự xử lý phần thay đổi nội dung.


### 3. 
