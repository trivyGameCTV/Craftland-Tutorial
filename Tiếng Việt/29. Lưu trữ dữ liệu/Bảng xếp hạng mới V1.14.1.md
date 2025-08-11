

# Bảng xếp hạng mới - Nội bộ

## Tài liệu liên quan

[Giới thiệu mô-đun lưu trữ dữ liệu phiên bản trước: Tiếng Trung giản thể](https://ffcraftland-pre.garena.com/zh-cn/tutorial/fe/1-35/)

[Giới thiệu mô-đun lưu trữ dữ liệu của các phiên bản trước: Tiếng Anh](https://ffcraftland.garena.com/en/tutorial/fe/1-35/)

[Giới thiệu mô-đun lưu trữ dữ liệu của các phiên bản trước: Tiếng Việt](https://ffcraftland.garena.com/vn/tutorial/fe/1-35/)

Tiếng Anh và Tiếng Việt được dịch từ phiên bản Tiếng Trung giản thể bằng Google Dịch, độ chính xác có thể không chính xác.



## Mô-đun lưu trữ dữ liệu

Đã được giới thiệu chi tiết trong tài liệu trên, ở đây chỉ giới thiệu sơ lược về mô-đun lưu trữ dữ liệu. Lưu trữ dữ liệu là một mô-đun tùy chọn, sau khi kích hoạt, cho phép nhà phát triển bản đồ sử dụng bảng dữ liệu trên máy chủ để lưu trữ dữ liệu, thường được sử dụng cho các chức năng như đồng bộ hóa dữ liệu giữa các bản đồ, giữa các trận đấu, bảng xếp hạng, v.v.Bài viết này sẽ tập trung giới thiệu việc sử dụng bảng dữ liệu lưu trữ mới cho chức năng bảng xếp hạng.

### Cổng vào

Tải mô-đun lưu trữ dữ liệu từ danh sách mô-đun để bắt đầu cấu hình thông tin cột cho bốn bảng dữ liệu:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806162055343.png" alt="image-20250806162055343" style="zoom:67%;" />

## Giới thiệu bảng mới

Giống như tất cả các bảng dữ liệu, mỗi bảng bạn cần chỉ định một cột "Key", tức là khóa chính (Primary Key) của bảng. Dữ liệu trong cột Key phải duy nhất và là cột chỉ mục của toàn bộ bảng. Bằng cách tra cứu Key, bạn có thể xác định hàng dữ liệu cụ thể trong bảng đã chỉ định. Khi chỉnh sửa nhiều lần các hàng dữ liệu có cùng Key bằng các biểu tượng, dữ liệu được chỉnh sửa sau sẽ luôn ghi đè lên dữ liệu trước đó.

### Bảng xếp hạng

Bảng xếp hạng là một loại bảng đa cột đặc biệt, bạn có thể tùy chỉnh một số cột để lưu trữ thông tin bổ sung, chẳng hạn như điểm số, thời gian tồn tại, tổng thời gian chơi, v.v. Tuy nhiên, bảng xếp hạng phải có một cột dữ liệu (cột Value) để sắp xếp theo thứ tự tăng dần hoặc giảm dần.

![image-20250806170632723](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806170632723.png)

Chọn UID làm Key, bảng xếp hạng sẽ tự động chuyển đổi cột Key thành thẻ người chơi:

![image-20250806170721219](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806170721219.png)

#### Bảng minh họa

Bảng dữ liệu xếp hạng 1

| Xếp hạng | Key | Giá trị | Cột tùy chỉnh 1 | Cột tùy chỉnh 2 | Cột tùy chỉnh… |
| ---- | ------------ | ----- | -------------------------- | ----------- | ------------ |
| 1 | Player1 UUID | 100 | bất kỳ giá trị nào bạn muốn lưu trữ | | |
| 2 | Player2 UUID | 90 | | | |

### Bảng dữ liệu nhiều cột

Bảng nhiều cột là một loại bảng hỗ trợ dữ liệu nhiều cột (khác với bảng dữ liệu trước đây chỉ hỗ trợ một cột dữ liệu). Bạn có thể lưu trữ nhiều loại dữ liệu dưới một Key. Trong script đồ họa, còn cung cấp API để chỉnh sửa bảng xếp hạng và bảng liên quan. Khi Key trùng nhau (ví dụ: đều là UUID của người chơi), có thể chỉnh sửa đồng thời bảng xếp hạng và bảng dữ liệu nhiều cột thông qua một đối tượng đồ họa cụ thể.

![image-20250806170813281](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806170813281.png)

#### Bảng minh họa

Bảng dữ liệu nhiều cột 1

| Key | Value | Custom Col1 | Custom Col2 | Custom Col…… |
| ------------ | ----- | -------------------------- | ----------- | ------------ |
| Player1 UUID | 100 | bất kỳ giá trị nào bạn muốn lưu trữ | | |
| Player2 UUID | 90 | | | |



## Chức năng bảng xếp hạng

### Kích hoạt chức năng

Để kích hoạt chức năng bảng xếp hạng, bạn phải kích hoạt mô-đun lưu trữ dữ liệu trong dự án và tạo ít nhất một bảng dữ liệu bảng xếp hạng.

Sau khi chuẩn bị xong, trong giao diện bản đồ phát hành của [Trung tâm nhà phát triển](https://craftland.garena.com/), chỉnh sửa bản đồ sắp phát hành để xem các thiết lập liên quan đến bảng xếp hạng:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806164442617.png" alt="image-20250806164442617" style="zoom: 67%;" />

Kích hoạt tính năng này, giao diện chi tiết bản đồ của bạn sẽ hiển thị nút bảng xếp hạng, người chơi có thể xem thông tin bảng xếp hạng mà bạn đã chỉnh sửa tại đây:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806171313422.png" alt="image-20250806171313422" style="zoom:67%;" />

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806164728942.png" alt="image-20250806164728942" style="zoom:67%;" />

### Chỉnh sửa bảng xếp hạng

Trong giao diện chỉnh sửa bảng xếp hạng của bản đồ đã đăng ở trên, bạn có thể và hiện tại chỉ có thể chọn một bảng dữ liệu để hiển thị thông tin bảng xếp hạng. (Mặc dù bạn có thể sử dụng nhiều bảng trong dự án để lưu trữ dữ liệu)

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806164912096.png" alt="image-20250806164912096" style="zoom:67%;" />

Sau đó, bạn có thể chỉnh sửa các nội dung khác của bảng xếp hạng: bao gồm việc hiển thị bảng xếp hạng bên ngoài, sử dụng các cột nào làm kiểu hiển thị cho bảng xếp hạng và thứ tự của chúng.

Chọn nhiều ngôn ngữ, bạn có thể chỉnh sửa thủ công thông tin ngôn ngữ của tiêu đề bảng xếp hạng:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806173701944.png" alt="image-20250806173701944" style="zoom:67%;" />

Các ngôn ngữ không được điền sẽ sử dụng tên cột mặc định của bảng.

Sau khi chỉnh sửa hoàn tất, trang thông tin bản đồ sẽ hiển thị bảng xếp hạng hiện tại của bạn, các ngôn ngữ đa ngôn ngữ sẽ không hiển thị trong bảng xếp hạng:

![image-20250806165547462](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806165547462.png)

## Công cụ chia sẻ hình ảnh nội bộ

Ngoài ra, bạn cũng có thể chỉnh sửa bảng xếp hạng trong công cụ chia sẻ hình ảnh nội bộ, với logic tương tự như trung tâm dữ liệu:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250808170839804.png" alt="image-20250808170839804" style="zoom:67%;" />

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250808170852777.png" alt="image-20250808170852777" style="zoom: 67%;" />

## Biểu tượng

Sử dụng biểu tượng vào thời điểm thích hợp — ví dụ: khi người chơi đạt điểm, hoặc khi kết thúc mỗi ván đấu — để lưu trữ dữ liệu vào bảng xếp hạng.

![image-20250806165732042](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806165732042.png)

Lưu ý rằng các biểu tượng phải liên quan đến bảng xếp hạng, nếu không tham số SheetName sẽ không đọc được bảng dữ liệu xếp hạng đã tạo.

Để thuận tiện hơn trong việc chỉnh sửa hai loại bảng đa cột được giới thiệu trong bài hướng dẫn này, chúng tôi đã thêm Tuple, một loại danh sách đặc biệt. Loại Tuple hỗ trợ tự động nhận diện giá trị của bảng dữ liệu hoặc bảng xếp hạng đã chỉ định để tạo thành một danh sách đặc biệt với loại dữ liệu đã chỉ định.

![image-20250806174722968](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806174722968.png)

Tuple sẽ tự động đọc tất cả các bảng và sử dụng kiểu dữ liệu của các cột trong bảng làm kiểu dữ liệu cho các mục trong danh sách:

![image-20250806175459462](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806175459462.png)

Đối với bảng dữ liệu xếp hạng, sau khi tạo cột dữ liệu tùy chỉnh mới, giá trị thực tế sẽ chứa dữ liệu của N cột, do đó cũng tạo thành một tuple:

![image-20250806175601013](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806175601013.png)

Do đó, trong thực tế, tuple có thể có cấu trúc lồng nhau:

![image-20250806180055942](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806180055942.png)

Các nguyên tố tuple không tự động cập nhật thông tin như tên cột của bảng, vì vậy nếu có thay đổi, cần phải làm mới thủ công các nguyên tố tuple.

## Mã

Ví dụ mã:

1. Ghi

```go
WriteDBLeaderboardAssociationValue(``"rank"``, ``"test_uid_1"``, {``60``, ``"1:00"``}, ``""``, out var c, out var d)
```

2. Đọc

   ```go
   ReadDBLeaderboardAssociationValue(``"rank"``, ``"test_uid_1"``, out var data, ``""``, out var a, out var b)``var data_normal List<object> = data[``2``] as List<object>``LogWarning(data_normal[``1``])
   ```

### Danh sách API liên quan

1. SetTuple
2. GetTuple
3. WriteDBLeaderboardAssociationValue
4. RemoveFromLeaderboardDataStoreByKey
5. ReadDBLeaderboardAssociationValue
6. WriteToLeaderboardDataStore
7. RemoveFromLeaderboardDataStoreByKey
8. ReadFromLeaderboardDataStore

Đặc biệt, đối với hàm: ReadDBLeaderboardAssociationValue, giá trị trả về là một tuple:

**Kết quả:** Loại là **{rankname_value}Tuple**

**{rank, key, value}**

- rank: int
- key: string
- value: tuple
  - **{value, GameCompletionTime}**

Đối với hàm: WriteDBLeaderboardAssociationValue, đối với các tham số Key và Value:

- **Key:** Khuyến nghị chuyển đổi UID của người chơi thành chuỗi ký tự làm khóa, để tên hiển thị của người chơi có thể hiển thị trong Craftland
- **Value：** Kiểu là **{rankname} Tuple**. Sau khi chọn SheetName, nhấp đúp vào Value để nhanh chóng thêm khối tương ứng

Để biết thêm thông tin về tham số và mô tả của các API khác, vui lòng tham khảo: [Trang tài liệu chính thức](https://ffcraftland.garena.com/en/docs/api)

## Gỡ lỗi cục bộ

Khi chỉnh sửa bản đồ, không thể truy cập dữ liệu của người chơi trực tuyến, nhưng Craftland Studio PC cung cấp cách xem dữ liệu được lưu trữ trong quá trình gỡ lỗi thông qua tệp JSON cục bộ.

![image-20250806170248163](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806170248163.png)

Sau khi dữ liệu được lưu trữ trong quá trình gỡ lỗi, nhấp vào tùy chọn trong hình để chuyển đến thư mục JSON cục bộ. Thông tin bảng dữ liệu sẽ được lưu trữ dưới dạng JSON, cho phép nhà phát triển kiểm tra logic có chính xác hay không.

![image-20250806170420358](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806170420358.png)
