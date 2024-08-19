# Hướng Dẫn Sử Dụng Kịch Bản Đồ Họa

Bài viết này giới thiệu cách chỉnh sửa kịch bản đồ họa.

## Giải Thích Giao Diện

![image-20240719154714450](./img/image-20240719154714450.png)

1. **Canvas**: Khu vực chỉnh sửa chính.
2. **Tệp hiện đang chỉnh sửa**.
3. **Phân loại các nút**, nhấp vào bất kỳ nút nào để mở giao diện chọn nút.
4. **Bảng thuộc tính**.

## Giải Thích Phân Loại Nút

Các loại nút tương ứng với khu vực 3 là:

1. **Tìm kiếm**: Tìm kiếm nút bằng cách nhập từ khóa.
2. **Thường dùng**: Những nút được đánh dấu là thường dùng sẽ xuất hiện ở đây.
3. **Sự kiện**: Được kích hoạt khi thỏa mãn điều kiện, là điểm khởi đầu của logic.
4. **Điều kiện**: Dùng để kiểm soát luồng kịch bản.
5. **Hành vi**: Thao tác thực tế trên thực thể hoặc dữ liệu.
6. **Mô-đun**: Một số hành vi độc quyền của mô-đun.
7. **Dữ liệu**: Xử lý dữ liệu.
8. **Biến**: Sử dụng hoặc thêm biến.
9. **Hàm**: Sử dụng hoặc tạo hàm tùy chỉnh mới.
10. **Gọi bên ngoài**: Gọi hàm tùy chỉnh từ kịch bản khác.

## Sử Dụng Các Nút

### Giải Thích Về Nút

Phần nhô ra bên dưới của nút biểu thị rằng có thể liên kết nút này với các nút khác sau nó.

![image-20240719162414368](./img/image-20240719162414368.png)

Phần lõm ở phía trên của nút biểu thị rằng có thể liên kết nút này với các nút trước đó, và chỉ khi nút trước chạy thì nút này mới chạy.

![image-20240719162458868](./img/image-20240719162458868.png)

Nếu phía trên không có lõm nhưng phía dưới có nhô ra, điều đó biểu thị rằng nút này là điểm bắt đầu của một đoạn logic, thường là nút sự kiện.

![image-20240719162532230](./img/image-20240719162532230.png)

Nếu cả trên và dưới đều không có nhô ra hay lõm, nút này biểu thị một đoạn dữ liệu, có thể được áp dụng cho các nút khác.

![image-20240719162637872](./img/image-20240719162637872.png)

Nút sẽ có tham số đầu vào và đầu ra:

**Tham số đầu vào**:

Tham số đầu vào mặc định là trống, loại bên trong được chỉ định là loại tham số cần thiết.

![image-20240719163219101](./img/image-20240719163219101.png)

> Tên kịch bản cũng là tham số cần thiết, nhưng sử dụng công cụ chọn tài nguyên nên có thể trực tiếp chọn tài nguyên trong dự án mà không cần lo lắng về việc khớp loại.

**Tham số đầu ra**:

Tham số đầu ra mặc định là một ô vuông màu, có thể kéo ô này để điền vào khung tham số đầu vào cần thiết.

![image-20240719163455421](./img/image-20240719163455421.png)

### Sử Dụng Nút

Chọn nút muốn sử dụng từ danh mục, sau đó nhấp hoặc kéo vào canvas để sử dụng nút tương ứng.

![image-20240719161426471](./img/image-20240719161426471.png)

![image-20240719161444643](./img/image-20240719161444643.png)

Sử dụng các nút có rãnh phía trên để ghép nối hai nút lại với nhau:

![image-20240719161910607](./img/image-20240719161910607.png)

![image-20240719161930593](./img/image-20240719161930593.png)

Logic của một nhóm nút luôn được thực hiện từ trên xuống dưới:

![image-20240719162112429](./img/image-20240719162112429.png)

![image-20240719162305301](./img/image-20240719162305301.png)

Với một nhóm nút được nối tiếp, các tham số đầu vào cần được điền bằng dữ liệu phù hợp để đảm bảo kịch bản hoạt động bình thường. Các biến không phù hợp sẽ báo lỗi, nhấp chuột vào thông báo lỗi để xem chi tiết.

![image-20240719163823327](./img/image-20240719163823327.png)

![image-20240719163854644](./img/image-20240719163854644.png)

## Kiểm Soát Luồng

Mặc định, kịch bản đồ họa được thực hiện theo thứ tự từ trên xuống dưới. Bạn có thể cần kiểm soát luồng để thực hiện các logic phức tạp hơn.

Xin tham khảo phần kiểm soát luồng của kịch bản đồ họa trong liên kết dưới đây để biết thêm chi tiết:

[Hướng dẫn bổ sung về kịch bản - User Manual.md](./脚本附加说明-用户手册.md)

## Biến

Bạn có thể định nghĩa hoặc chỉnh sửa ba loại biến:

1. **Thuộc tính thực thể toàn cầu**: Thuộc tính của các thành phần toàn cầu, hỗ trợ tùy chỉnh. Có thể lấy hoặc chỉnh sửa thuộc tính này trong bất kỳ kịch bản nào.
2. **Biến kịch bản**: Chỉ được sử dụng trong kịch bản hiện tại, các kịch bản khác có thể lấy và chỉnh sửa biến này thông qua gọi bên ngoài.
3. **Biến cục bộ**: Chỉ được sử dụng trong khối mã hiện tại, không có hiệu lực ngoài khối mã.

### Thuộc Tính Thực Thể Toàn Cầu

Thông qua cài đặt thành phần, bạn có thể thêm thuộc tính thực thể toàn cầu.

![image-20240719170731723](./img/image-20240719170731723.png)

![image-20240719170751222](./img/image-20240719170751222.png)

![image-20240719170812335](./img/image-20240719170812335.png)

Sau khi tạo xong thuộc tính thực thể toàn cầu, bạn có thể sử dụng nút "Lấy toàn cầu" để lấy thuộc tính này:

![image-20240719170915428](./img/image-20240719170915428.png)

Sử dụng nút "Thiết lập toàn cầu" để thiết lập thuộc tính này:

![image-20240719170953632](./img/image-20240719170953632.png)

### Biến Kịch Bản

Trong danh mục biến, có một nút để tạo biến:

![image-20240719171622005](./img/image-20240719171622005.png)

![image-20240719171647910](./img/image-20240719171647910.png)

Biến được tạo theo cách này là biến kịch bản, dùng để xử lý dữ liệu trong kịch bản hiện tại.

Trong các kịch bản khác, bạn có thể lấy và thiết lập biến này thông qua cách gọi bên ngoài:

![image-20240719171819031](./img/image-20240719171819031.png)

> Lưu ý khi gọi bên ngoài từ kịch bản khác: cần chỉ định thực thể gắn kịch bản khi lấy và thiết lập biến.

### Biến Cục Bộ

Bạn có thể tạo biến chỉ sử dụng được trong khối mã hiện tại thông qua nút biến cục bộ:

![image-20240719171508081](./img/image-20240719171508081.png)

Bạn có thể đổi tên biến này bằng cách nhấp đúp vào tên biến:

![image-20240719171540482](./img/image-20240719171540482.png)

Khối mã là một đoạn kịch bản liên tục. Đáng lưu ý là các nút "Nếu - Nếu không" trong danh mục điều kiện được chia thành hai khối mã. Mỗi đoạn "Nếu", "Nếu không", và "Nếu không nếu" là một khối mã độc lập.

![image-20240722192115698](./img/image-20240722192115698.png)

![image-20240722192055277](./img/image-20240722192055277.png)

## Hàm Tùy Chỉnh và Sử Dụng

Kịch bản đồ họa hỗ trợ các hàm có giá trị trả về và không có giá trị trả về.

Các hàm có giá trị trả về không thể liên kết với các nút khác khi được gọi, nút gọi chính là giá trị trả về.

![image-20240719180031043](./img/image-20240719180031043.png)

![image-20240719180117743](./img/image-20240719180117743.png)

Các hàm không có giá trị trả về có thể liên kết với các nút khác khi được gọi.

![image-20240719180039563](./img/image-20240719180039563.png)

![image-20240719180134147](./img/image-20240719180134147.png)

**Chờ đợi**: Nút này chặn các hàm không đồng bộ, đợi hàm không đồng bộ thực thi xong mới thực hiện các nút tiếp theo.

**Thực thi**: Nút này không chặn các hàm không đồng bộ, tiếp tục thực hiện các nút tiếp theo.

Hàm không đồng bộ là hàm mà trong đó sử dụng các nút sẽ thực hiện xử lý không đồng bộ, ví dụ như "Chờ đợi".

![image-20240722105341566](./img/image-20240722105341566.png)

**Lưu ý**: Không hỗ trợ sử dụng các nút không đồng bộ trong hàm có giá trị trả về.

![image-20240806115625031](./img/image-20240806115625031.png)

Nếu cần giá trị trả về của hàm không đồng bộ, hãy sử dụng hàm không có giá trị trả về và sử dụng biến đầu ra.

![image-20240806115658582](./img/image-20240806115658582.png)

Dù có hay không có giá trị trả về, hàm tùy chỉnh vẫn có thể sử dụng biến đầu ra của hàm ở phía dưới nút gọi hàm để lấy kết quả đầu ra.

![image-20240806113746376](./img/image-20240806113746376.png)

![image-20240806121329099](./img/image-20240806121329099.png)

## Tìm Kiếm Nút và Sử Dụng Nút Thường Dùng

Nhập từ khóa có thể tìm kiếm ra nút tương ứng.

![image-20240719181845696](./img/image-20240719181845696.png)

Trong giao diện chọn nút, nhấp chuột phải vào nút để đặt nút làm nút thường dùng. Trong danh mục nút thường dùng có thể sử dụng nút một cách nhanh chóng.

![image-20240719182033312](./img/image-20240719182033312.png)

![image-20240719182130450](./img/image-20240719182130450.png)

## Ví Dụ

Sử dụng một ví dụ đơn giản để minh họa cách sử dụng kịch bản:

Thiết kế như sau:

1. Mỗi người chơi khi tham gia cuộc thi sẽ được cấp một khẩu M4A1.
2. Khi người chơi bắn, mỗi lần bắn sẽ trừ 1 điểm sinh mệnh của người chơi.

**Tạo Kịch Bản**:

Yêu cầu 1 là toàn cục, yêu cầu 2 là cho từng người chơi. Vì vậy, cần gắn một kịch bản vào toàn cục và một kịch bản vào mỗi người chơi. Cả việc cấp vật phẩm và trừ sinh mệnh đều cần được server biết, do đó cả hai đều được tạo dưới dạng kịch bản server.

![image-20240719183317332](./img/image-20240719183317332.png)

![image-20240719183333435](./img/image-20240719183333435.png)

**Chỉnh Sửa Kịch Bản**:

Đối với yêu cầu 1, cần thực hiện việc cấp vật phẩm mỗi khi người chơi tham gia cuộc thi:

![image-20240719183627320](./img/image-20240719183627320.png)

Với nút thêm vật phẩm, cần thêm ba tham số: mục tiêu thêm vật phẩm, vật phẩm được thêm, và số lượng vật phẩm.

Mục tiêu thêm vật phẩm chính là người chơi đã kích hoạt sự kiện khi tham gia cuộc thi, vật phẩm được chọn qua trình quản lý tài nguyên là M4A1, và số lượng là 1.

![image-20240719183756275](./img/image-20240719183756275.png)

Đối với yêu cầu 2, mỗi khi bắn cần thực hiện việc trừ điểm sinh mệnh:

Chúng ta nhận thấy thực tế không có nút trừ điểm sinh mệnh:

![image-20240719183925677](./img/image-20240719183925677.png)

> Tham số phục hồi sinh mệnh điền số âm sẽ không trừ sinh mệnh.

Tuy nhiên, vì sinh mệnh là một thuộc tính của người chơi, ta có thể điều chỉnh thông qua việc thiết lập thuộc tính:

![image-20240719184034769](./img/image-20240719184034769.png)

Nút thiết lập thuộc tính yêu cầu các tham số: thực thể được thiết lập thuộc tính, thuộc tính được thiết lập và giá trị cũng như phép toán.

Trong đó, thực thể được thiết lập thuộc tính chính là người chơi hiện tại, do đó có thể sử dụng thực thể này, nhấp đúp vào vị trí tham số để nhanh chóng điền thực thể này.

![image-20240719184236329](./img/image-20240719184236329.png)

Thuộc tính cần thay đổi là sinh mệnh hiện tại, chọn sinh mệnh hiện tại.

Giá trị được thiết lập là sinh mệnh hiện tại trừ 1, do đó cần lấy sinh mệnh hiện tại.

![image-20240719184443713](./img/image-20240719184443713.png)

Sử dụng phép trừ trong danh mục dữ liệu để trừ đi 1, sau đó điền vào tham số:

![image-20240719184604249](./img/image-20240719184604249.png)

![image-20240719184622223](./img/image-20240719184622223.png)

Cũng có thể sử dụng phép toán của nút thiết lập thuộc tính để thực hiện logic này:

![image-20240719184700828](./img/image-20240719184700828.png)

Chạy và gỡ lỗi để xem kết quả:

![image-20240719184826220](./img/image-20240719184826220.png)

> Mỗi người đều được cấp một khẩu M4A1.

![image-20240719184935284](./img/image-20240719184935284.png)

> Bắn 8 lần thì mất 8 điểm sinh mệnh.
>
> Khi bắn, sự kiện này được kích hoạt mỗi lần thực hiện lệnh bắn. Với vũ khí bắn liên thanh, các lần bắn liên tục trước khi đặt vũ khí xuống được tính là một lần bắn, và sự kiện chỉ kích hoạt một lần.
