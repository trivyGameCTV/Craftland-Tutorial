# AVATAR - Hướng dẫn sử dụng

# Nhóm ngoại hình

Nhóm ngoại hình là khái niệm quản lý phân loại mesh ngoại hình trong mô hình.

![image-20241011143752628](./img/image-20241011143752628.png)

Thêm mô hình có xương vào làm prefab, bạn có thể vào chỉnh sửa ngoại hình:

![image-20241011144305585](./img/image-20241011144305585.png)

Trong cài đặt nhóm ngoại hình, bạn có thể đặt nhóm này là một trong các ngoại hình loại trừ lẫn nhau:

![image-20241011153210375](./img/image-20241011153210375.png)

Tất cả các nhóm ngoại hình được đặt vào cùng một nhóm loại trừ sẽ không hiển thị đồng thời. Điều này tiện lợi cho việc chuyển đổi skin và các thao tác khác.

Trong nhóm ngoại hình, các bộ phận được tính theo đơn vị mesh, số lượng mesh của một mô hình được xác định khi tạo mô hình.

![image-20241011153357270](./img/image-20241011153357270.png)

Trong cài đặt mesh, bạn có thể chỉnh sửa điểm nối với xương, cách thức kết nối; chỉnh sửa cách thức render và các thao tác khác:

![image-20241011153506396](./img/image-20241011153506396.png)

Có thể thêm mesh mới cho mô hình bằng cách tạo ngoại hình mới:

![image-20241011163120786](./img/image-20241011163120786.png)

Có thể chọn tài nguyên mesh có sẵn trong dự án:

![image-20241011163249400](./img/image-20241011163249400.png)

Nếu mesh mới thêm không khớp với xương gốc, hãy chọn cách kết nối là liên kết:

![image-20241011163331947](./img/image-20241011163331947.png)

![image-20241011163417536](./img/image-20241011163417536.png)

# Sử dụng nhóm ngoại hình

Thông qua script, bạn có thể điều khiển việc ẩn/hiện hoặc chuyển đổi nhóm ngoại hình cụ thể.

![image-20241011144706308](./img/image-20241011144706308.png)

> Chuyển đổi nhóm ngoại hình sẽ ẩn nhóm cũ và hiển thị nhóm mới.

Trong thú cưng ngoài hành tinh có hai mesh, lần lượt là thân ngoài hành tinh và đĩa bay:

![image-20241011153600498](./img/image-20241011153600498.png)

Chúng tôi tạo nhóm ngoại hình mới để tách hai phần này ra:

![image-20241011153629170](./img/image-20241011153629170.png)

Ở trạng thái mặc định, chúng tôi ẩn đĩa bay và hiển thị nó sau khi vòng chơi bắt đầu:

![image-20241011153714874](./img/image-20241011153714874.png)

![image-20241011153746239](./img/image-20241011153746239.png)

> Script toàn cục

Trong giai đoạn chuẩn bị của trò chơi, chỉ thấy ngoài hành tinh:

![image-20241011153918797](./img/image-20241011153918797.png)

Sau khi vòng chơi bắt đầu, đĩa bay được hiển thị:

![image-20241011153933339](./img/image-20241011153933339.png)

Sử dụng linh hoạt script để điều khiển nhóm ngoại hình, bạn có thể thực hiện các thao tác như chuyển đổi hiển thị bộ phận, thay đổi skin, biến hình trong điều kiện cụ thể.
