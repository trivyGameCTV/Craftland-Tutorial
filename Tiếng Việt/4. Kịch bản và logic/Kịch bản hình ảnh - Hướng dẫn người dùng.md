# Tập lệnh Đồ họa - Hướng dẫn sử dụng

Bài viết này giới thiệu phương pháp chỉnh sửa tập lệnh đồ họa.

## Giải thích giao diện

![image-20240719154714450](./img/image-20240719154714450.png)

1. Canvas, khu vực chỉnh sửa chính
2. Tệp hiện đang chỉnh sửa
3. Phân loại nút, nhấp vào bất kỳ nút nào sẽ mở giao diện chọn nút
4. Bảng thuộc tính

## Giải thích phân loại nút

Phân loại nút tương ứng với khu vực 3:

1. Tìm kiếm: Nút được tìm kiếm bằng cách nhập từ khóa.
2. Thường dùng: Nút được đặt làm thường dùng sẽ xuất hiện ở đây.
3. Sự kiện: Kích hoạt khi điều kiện được thỏa mãn, là điểm bắt đầu của logic.
4. Điều kiện: Dùng để kiểm soát luồng của tập lệnh.
5. Hành vi: Thao tác thực tế trên thực thể/dữ liệu.
6. Mô-đun: Một số hành vi riêng của mô-đun.
7. Dữ liệu: Xử lý dữ liệu.
8. Biến: Sử dụng hoặc thêm biến mới.
9. Hàm: Sử dụng hoặc tạo mới hàm tùy chỉnh.
10. Gọi bên ngoài: Gọi hàm tùy chỉnh từ tập lệnh khác.

## **Sử dụng nút**

### Giải thích nút

Phần nhô ra dưới nút đại diện cho việc nút đó có thể liên kết với các nút khác sau nó.

![image-20240719162414368](./img/image-20240719162414368.png)

Phần lõm trên nút đại diện cho việc nút đó có thể liên kết với các nút trước nó và chỉ chạy sau khi các nút trước đó đã chạy.

![image-20240719162458868](./img/image-20240719162458868.png)

Nếu không có phần lõm trên nhưng có phần nhô ra dưới, đại diện cho việc nút đó là điểm bắt đầu của một đoạn logic, thường là nút sự kiện.

![image-20240719162532230](./img/image-20240719162532230.png)

Nếu không có phần nhô ra hoặc lõm nào, đại diện cho việc nút đó là một đoạn dữ liệu, có thể áp dụng vào các nút khác.

![image-20240719162637872](./img/image-20240719162637872.png)

Nút sẽ có tham số đầu vào và đầu ra:

**Tham số đầu vào**:

Tham số đầu vào mặc định là trống, loại được ghi chú bên trong là loại tham số cần thiết.

![image-20240719163219101](./img/image-20240719163219101.png)

> Tên tập lệnh cũng là tham số cần thiết, nhưng sử dụng bộ chọn tài nguyên, có thể chọn trực tiếp tài nguyên trong dự án mà không cần lo về việc khớp loại.

**Tham số đầu ra**:

Tham số đầu ra mặc định là ô màu, có thể kéo ô này vào khung tham số đầu vào cần thiết:

![image-20240719163455421](./img/image-20240719163455421.png)

### Sử dụng nút

Chọn nút muốn sử dụng trong phân loại, sau đó nhấp hoặc kéo vào canvas để sử dụng nút tương ứng.

![image-20240719161426471](./img/image-20240719161426471.png)

![image-20240719161444643](./img/image-20240719161444643.png)

Sử dụng các nút có rãnh trên để ghép hai nút lại với nhau:

![image-20240719161910607](./img/image-20240719161910607.png)

![image-20240719161930593](./img/image-20240719161930593.png)

Một nhóm logic của các nút luôn từ trên xuống dưới:

![image-20240719162112429](./img/image-20240719162112429.png)

![image-20240719162305301](./img/image-20240719162305301.png)

Đối với một nhóm các nút được nối tiếp nhau, tham số đầu vào cần thiết phải được điền bằng dữ liệu phù hợp để đảm bảo tập lệnh hoạt động bình thường. Biến không phù hợp sẽ báo lỗi, nhấp chuột vào lỗi để xem thông tin lỗi:

![image-20240719163823327](./img/image-20240719163823327.png)

![image-20240719163854644](./img/image-20240719163854644.png)

## Kiểm soát luồng

Thứ tự thực thi mặc định của tập lệnh đồ họa là từ trên xuống dưới, bạn có thể cần kiểm soát luồng mã để thực hiện logic phức tạp.

Vui lòng tham khảo liên kết dưới đây để xem chi tiết về kiểm soát luồng trong tập lệnh đồ họa:

 [Hướng dẫn bổ sung - Hướng dẫn sử dụng.md](./Hướng dẫn bổ sung - Hướng dẫn sử dụng.md) 

## Biến

Trong phần biến có thể định nghĩa hoặc chỉnh sửa ba loại biến:

1. Thuộc tính thực thể toàn cục: Thuộc tính của thành phần toàn cục, hỗ trợ tùy chỉnh. Có thể lấy hoặc chỉnh sửa thuộc tính thực thể toàn cục tùy chỉnh trong bất kỳ tập lệnh nào.
2. Biến tập lệnh: Chỉ dùng cho tập lệnh hiện tại, các tập lệnh khác có thể lấy và chỉnh sửa thông qua gọi bên ngoài.
3. Biến cục bộ: Chỉ dùng cho khối mã hiện tại, không hợp lệ ngoài khối mã.

### Thuộc tính thực thể toàn cục

Thông qua thuộc tính thành phần trong cài đặt thành phần, có thể thêm thuộc tính thực thể toàn cục.

![image-20240719170731723](./img/image-20240719170731723.png)

![image-20240719170751222](./img/image-20240719170751222.png)

![image-20240719170812335](./img/image-20240719170812335.png)

Sau khi tạo xong thuộc tính thực thể toàn cục, bạn có thể sử dụng lấy thuộc tính toàn cục để lấy thuộc tính này:

![image-20240719170915428](./img/image-20240719170915428.png)

Sử dụng đặt thuộc tính toàn cục để đặt thuộc tính này:

![image-20240719170953632](./img/image-20240719170953632.png)

### Biến tập lệnh

Trong phân loại biến, tồn tại một nút tạo biến:

![image-20240719171622005](./img/image-20240719171622005.png)

![image-20240719171647910](./img/image-20240719171647910.png)

Biến được tạo theo cách này là biến tập lệnh, dùng cho xử lý dữ liệu trong tập lệnh hiện tại.

Trong các tập lệnh khác có thể lấy và đặt biến này thông qua gọi bên ngoài:

![image-20240719171819031](./img/image-20240719171819031.png)

> Khi gọi bên ngoài từ các tập lệnh khác cần chú ý: Khi lấy và đặt cần chỉ định thực thể mà tập lệnh được gắn vào.

### Biến cục bộ

Thông qua đồ họa biến cục bộ có thể tạo biến chỉ dùng cho khối mã hiện tại:

![image-20240719171508081](./img/image-20240719171508081.png)

Có thể đổi tên biến bằng cách nhấp đúp vào tên biến:

![image-20240719171540482](./img/image-20240719171540482.png)

Khối mã là một đoạn liên tục của đồ họa, đặc biệt lưu ý rằng đồ họa "nếu-không thì" trong phân loại điều kiện mặc định là hai khối mã. Mỗi đoạn nếu, không thì, nếu không thì đều là một khối mã độc lập.

![image-20240722192115698](./img/image-20240722192115698.png)

![image-20240722192055277](./img/image-20240722192055277.png)



## Hàm tùy chỉnh và sử dụng

Trong tập lệnh đồ họa hỗ trợ hàm có giá trị trả về và hàm không có giá trị trả về.

Hàm có giá trị trả về khi gọi không thể liên kết với các nút khác, đồ họa gọi chính là giá trị trả về.

![image-20240719180031043](./img/image-20240719180031043.png)

![image-20240719180117743](./img/image-20240719180117743.png)

Hàm không có giá trị trả về khi gọi có thể liên kết với các nút khác.

![image-20240719180039563](./img/image-20240719180039563.png)
![image-20240719180134147](./img/image-20240719180134147.png)

等待: Khi nút này là hàm bất đồng bộ, sẽ chặn lại và chờ hàm bất đồng bộ thực thi xong rồi mới thực thi nút tiếp theo.

Thực thi: Khi nút này là hàm bất đồng bộ, không chặn lại mà tiếp tục thực thi nút tiếp theo.

Hàm bất đồng bộ là hàm sử dụng các nút xử lý bất đồng bộ, ví dụ như "chờ đợi".

![image-20240722105341566](./img/image-20240722105341566.png)

**Chú ý**: Không hỗ trợ sử dụng nguyên tố bất đồng bộ trong các hàm có giá trị trả về.

![image-20240806115625031](./img/image-20240806115625031.png)

Nếu cần giá trị trả về từ hàm bất đồng bộ, hãy sử dụng hàm không có giá trị trả về và dùng biến đầu ra.

![image-20240806115658582](./img/image-20240806115658582.png)

Dù có hay không có giá trị trả về, hàm tùy chỉnh đều có thể sử dụng biến đầu ra của hàm để lấy kết quả ở dưới nguyên tố gọi hàm.

![image-20240806113746376](./img/image-20240806113746376.png)

![image-20240806121329099](./img/image-20240806121329099.png)

## Tìm kiếm và sử dụng thường xuyên các nút

Nhập từ khóa để tìm kiếm các nút tương ứng

![image-20240719181845696](./img/image-20240719181845696.png)

Trong giao diện chọn nút, nhấp chuột phải vào nút để đặt làm nút thường dùng, trong danh mục nút thường dùng có thể nhanh chóng sử dụng nút.

![image-20240719182033312](./img/image-20240719182033312.png)

![image-20240719182130450](./img/image-20240719182130450.png)

## Ví dụ

Sử dụng một ví dụ đơn giản để minh họa cách dùng script:

Thiết kế như sau:

1. Mỗi người chơi khi tham gia trận đấu sẽ được phát một khẩu M4A1.
2. Khi người chơi bắn, mỗi lần bắn sẽ trừ 1 điểm sinh mệnh của bản thân.

**Tạo script**:

1. là yêu cầu toàn cục, 2. là cho từng người chơi. Vì vậy cần gắn một script trên toàn cục và một trên từng người chơi. Phát vật phẩm và trừ sinh mệnh đều cần server biết, nên đều tạo thành script server.

![image-20240719183317332](./img/image-20240719183317332.png)

![image-20240719183333435](./img/image-20240719183333435.png)

**Chỉnh sửa script:**

Đối với 1, cần mỗi người chơi tham gia trận đấu đều thực hiện phát vật phẩm một lần:

![image-20240719183627320](./img/image-20240719183627320.png)

Đối với nút thêm vật phẩm, cần ba tham số: mục tiêu thêm vật phẩm, vật phẩm thêm vào và số lượng vật phẩm thêm vào.

Mục tiêu thêm vật phẩm chính là người chơi kích hoạt sự kiện tham gia trận đấu, vật phẩm chọn M4A1 từ trình quản lý tài nguyên, số lượng là 1.

![image-20240719183756275](./img/image-20240719183756275.png)

Đối với 2, mỗi lần bắn cần thực hiện trừ sinh mệnh một lần:

Chúng ta nhận thấy không có nút trừ sinh mệnh:

![image-20240719183925677](./img/image-20240719183925677.png)

> Điền số âm vào tham số của nút khôi phục sinh mệnh sẽ không trừ sinh mệnh

Tuy nhiên, sinh mệnh là một thuộc tính của người chơi, có thể điều chỉnh bằng cách đặt thuộc tính:

![image-20240719184034769](./img/image-20240719184034769.png)

Nút đặt thuộc tính cần các tham số: thực thể được đặt thuộc tính, thuộc tính được đặt và giá trị cùng phép toán.

Thực thể được đặt thuộc tính chính là người chơi hiện tại, nên có thể sử dụng thực thể này bằng cách nhấp đúp vào vị trí tham số để điền nhanh thực thể này.

![image-20240719184236329](./img/image-20240719184236329.png)

Thuộc tính cần thay đổi là sinh mệnh hiện tại, chọn sinh mệnh hiện tại.

Giá trị đặt là sinh mệnh hiện tại trừ đi 1, nên cần lấy sinh mệnh hiện tại.

![image-20240719184443713](./img/image-20240719184443713.png)

Sử dụng phép trừ trong phân loại dữ liệu để trừ đi một và điền tham số:

![image-20240719184604249](./img/image-20240719184604249.png)

![image-20240719184622223](./img/image-20240719184622223.png)

Cũng có thể trực tiếp sử dụng phép toán của nút đặt thuộc tính để thực hiện logic này:

![image-20240719184700828](./img/image-20240719184700828.png)

Chạy thử nghiệm để xem kết quả:

![image-20240719184826220](./img/image-20240719184826220.png)

> Mỗi người đều được phát một khẩu M4A1.

![image-20240719184935284](./img/image-20240719184935284.png)

> Bắn 8 lần mất 8 điểm sinh mệnh.
>
> Sự kiện kích hoạt khi bắn chỉ kích hoạt mỗi lần thực hiện lệnh bắn, vũ khí bắn liên tục trước khi hạ xuống chỉ tính là một lần bắn và chỉ kích hoạt sự kiện một lần. 