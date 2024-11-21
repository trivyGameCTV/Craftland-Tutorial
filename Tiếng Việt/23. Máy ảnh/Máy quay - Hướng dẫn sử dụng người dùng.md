# Hướng dẫn sử dụng camera

Người chơi sử dụng camera để quan sát trận đấu trong game, việc sử dụng các chế độ camera và thông số khác nhau có thể mang lại trải nghiệm hình ảnh khác biệt.

## Mô-đun camera

Mô-đun camera là mô-đun mặc định, không cần tải thêm.

![image-20240911182555100](./img/image-20240911182555100.png)

Bạn có thể cấu hình camera chính trong mô-đun camera.

## **Chế độ camera**

Trong mô-đun camera, sau khi chọn chế độ camera, bạn có thể điều chỉnh thêm các thông số của chế độ đó.

Trong các thông số, có một số thông số chung cho các chế độ camera:

![image-20240911182613203](./img/image-20240911182613203.png)

### Cấu hình chung

**Loại giới hạn góc xoay ống kính**: Chọn giữ nguyên logic gốc, camera sẽ giới hạn góc xoay của người chơi. Chọn WideRange, giới hạn này sẽ được nới lỏng.

**Phạm vi tầm nhìn**: Góc mà camera có thể nhìn thấy.

![image-20240910155604898](./img/image-20240910155604898.png)

**Chế độ che chắn**: Ngoài camera góc nhìn thứ nhất, cách xử lý khi có vật cản giữa camera và nhân vật người chơi. Có ba cách: cố định, đẩy gần và xuyên thấu.

![image-20240910164055112](./img/image-20240910164055112.png)

> Khi này, nếu tiếp tục xoay camera, nó sẽ bị tường chặn lại.

Trong chế độ cố định, dù có vật cản giữa camera và nhân vật người chơi cũng không xử lý.

![image-20240910164104396](./img/image-20240910164104396.png)

Trong chế độ đẩy gần, camera sẽ thay đổi vị trí của mình, như bị vật cản ép sát vào nhân vật người chơi.

![image-20240910164258233](./img/image-20240910164258233.png)

Trong chế độ xuyên thấu, nhân vật người chơi sẽ được đánh dấu bằng viền đỏ.

![image-20240910164454220](./img/image-20240910164454220.png)

**Chế độ chiếu**: Trong chế độ xuyên thấu, khi xử lý sự vật, camera sử dụng quy tắc gần lớn xa nhỏ như thực tế. Trong chế độ trực giao, quy tắc này không được áp dụng.

![image-20240910173104387](./img/image-20240910173104387.png)

> Chế độ xuyên thấu

![image-20240910173353307](./img/image-20240910173353307.png)

> Chế độ trực giao thường áp dụng cho game đi cảnh ngang có yêu cầu đặc biệt về cảnh quan.

**Độ lệch**: Trong các camera hỗ trợ thiết lập độ lệch, khi độ lệch là (0, 0, 0) thì đó là vị trí mặc định ban đầu của camera. Bằng cách điều chỉnh thông số này, bạn có thể điều chỉnh vị trí mặc định của camera.

### Camera góc nhìn thứ ba

Camera góc nhìn thứ ba có khoảng cách nhất định với người chơi và sẽ hiển thị nhân vật người chơi. Trong chế độ mặc định của camera góc nhìn thứ ba, người chơi có thể tự do xoay camera và lệnh di chuyển về phía trước của người chơi sẽ khiến nhân vật tiến về hướng mà camera đang quan sát.

![image-20240910170247388](./img/image-20240910170247388.png)

![image-20240910170300191](./img/image-20240910170300191.png)

> Nhân vật sẽ quay về hướng di chuyển trước rồi mới tiến lên.

#### FF cổ điển

FF cổ điển giống như trong game FreeFire với camera góc nhìn thứ ba. Chế độ FF cổ điển không thể thay đổi thông số.

#### Theo sau lưng

Camera theo sau lưng luôn hướng về phía sau lưng người chơi. Trong chế độ này, hướng ngang của nhân vật luôn bằng hướng ngang của camera và thao tác xoay camera cũng đồng thời xoay nhân vật người chơi.

### Camera góc nhìn thứ nhất

Vị trí của camera góc nhìn thứ nhất trùng với nhân vật người chơi, giống như quan sát thế giới game từ góc nhìn của nhân vật. Camera góc nhìn thứ nhất mặc định không hỗ trợ điều chỉnh phạm vi tầm nhìn.

#### Tài nguyên mới cho góc nhìn thứ nhất

Ở phần dưới của mô-đun, bạn có thể sử dụng tài nguyên mới cho góc nhìn thứ nhất.

![image-20240911182655142](./img/image-20240911182655142.png)

Khi tài nguyên mới cho góc nhìn thứ nhất được chọn, camera sẽ luôn hiển thị đôi tay thay vì chỉ hiển thị khi thực hiện hành động như trước đây.

#### FF cổ điển

Camera góc nhìn thứ nhất FF cổ điển giống với góc nhìn thứ nhất trong game FreeFire. Camera FF cổ điển có hiệu ứng động thay đổi phạm vi tầm nhìn khi di chuyển.

### Camera từ trên xuống

Camera từ trên xuống luôn hướng về mặt phẳng ngang trong trạng thái mặc định và sẽ theo dõi chuyển động của người chơi khi di chuyển.

![image-20240910175642062](./img/image-20240910175642062.png)

### Camera ngang

Camera ngang trong trạng thái mặc định luôn hướng về trục Z dương trong hệ tọa độ thế giới và sẽ di chuyển cùng với người chơi.

![image-20240910180227779](./img/image-20240910180227779.png)

Camera ngang có cấu hình độc đáo:

![image-20240911182724156](./img/image-20240911182724156.png)

**Góc nghiêng và góc ngang**: Có thể điều chỉnh góc ban đầu của camera. Sau khi cấu hình xong, camera sẽ giữ nguyên góc này.

**Có cho phép người chơi di chuyển theo trục X không**: Khi bật lên, lệnh di chuyển vào trong và ra ngoài màn hình sẽ bị chặn lại; người chơi chỉ có thể di chuyển sang hai bên trái phải của màn hình.

### Camera tự do

Trong chế độ camera tự do, lệnh di chuyển của người chơi sẽ điều khiển camera thay vì nhân vật. Trong trạng thái mặc định, điều khiển góc dọc của camera tự do bị đảo ngược.

![image-20240910180722654](./img/image-20240910180722654.png)

### Camera tùy chỉnh

Camera tùy chỉnh chỉ theo dõi người chơi mà không có chức năng khác; hiệu suất khi sử dụng phụ thuộc vào cấu hình của bạn.

![image-20240910181200118](./img/image-20240910181200118.png)

## Script

Ngoài việc cấu hình cho camera chính, sử dụng script có thể điều chỉnh động các thông số của camera hoặc tạo mới hay chuyển đổi giữa các camera.

![image-20240910190054154](./img/image-20240910190054154.png)

### Tạo & chuyển đổi camera

![image-20240910190216300](./img/image-20240910190216300.png)

Bằng cách tạo một camera mới nhưng chưa đưa vào sử dụng nên không làm thay đổi gì đến trải nghiệm của người chơi hiện tại. 

Sau khi tạo xong có thể điều chỉnh thuộc tính để thay đổi hiệu suất của nó. 

Sử dụng chức năng chuyển đổi để bắt đầu sử dụng một chiếc mới đã được chỉ định sẵn trước đó .

### Lớp phủ

Camera có thể chọn lọc render các đối tượng trên bản đồ hoặc nhân vật bằng cách thay đổi cấp lớp phủ. Tất cả đơn vị hiển thị đều có thành phần hiển thị .

![image - 2040910190543378 ](./img/image-20240910190543378.png)

Thiết lập cấp lớp phủ trong thành phần này , sau đó sửa đổi cấp lớp phủ mà máy ảnh sẽ render .

![image-2040910190647512](./img/image-20240910190647512.png)

> Theo mặc định , máy ảnh sẽ render tất cả các cấp lớp phủ ( 0 - 15 ) , nhưng không render cấp lớp phủ là 1 .

Bằng cách sửa đổi cấp lớp phủ , bạn có thể đạt được mục tiêu giấu đơn vị thuộc loại cụ thể , tiết kiệm hiệu suất , v.v .

Tuy nhiên , dù đơn vị không hiển thị nhưng vẫn tồn tại va chạm hoặc chức năng khác ; Người chơi vẫn bị chặn hoặc kích hoạt sự kiện va chạm bởi đối tượng không được render .
