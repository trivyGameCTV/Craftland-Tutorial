# Quản lý quy trình - .gitignore - Hướng dẫn người dùng

## Giới thiệu

Git là một hệ thống kiểm soát phiên bản phân tán mã nguồn mở, có thể xử lý hiệu quả và nhanh chóng từ các dự án rất nhỏ đến rất lớn. Tài liệu này chủ yếu dành cho những người đã sử dụng git để quản lý phiên bản, giới thiệu về chức năng gitignore và cấu hình gitignore do chính thức cung cấp.

### Gitignore là gì

Trong thư mục dự án, không phải tất cả các tập tin đều cần phải đồng bộ hóa với kho từ xa, chẳng hạn như cấu hình cá nhân, tập tin tạm thời. Sử dụng gitignore có thể đánh dấu những tập tin không cần Git theo dõi, tránh đồng bộ hóa quá mức và ghi đè các cài đặt cá nhân của cộng tác viên, từ đó nâng cao hiệu quả quản lý phiên bản của dự án.

## Tập tin .gitignore

`.gitignore` là một tập tin cấu hình văn bản thuần túy đặc biệt, chứa tất cả các tập tin hoặc thư mục cần phải bị bỏ qua trong dự án. Các tập tin hoặc thư mục được cấu hình trong tập tin `.gitignore` sẽ bị Git bỏ qua và không theo dõi.

Chúng tôi đã tạo tập tin này trong mỗi dự án theo mặc định và đã cấu hình các tập tin và thư mục nên bị bỏ qua.

Bạn có thể tìm thấy tập tin này trong dự án:

![image-20240724153902332](./img/image-20240724153902332.png)

Nếu bạn sử dụng hệ thống Linux, cần sử dụng cờ `-a` của lệnh `ls` để hiển thị các tập tin ẩn:

```defalut
ls -a
```

Cấu hình mặc định của tập tin là:

```default
.vscode/
Cache/
Libraries/
Temp/
*.lock
```
```markdown
Trong đó:

Tên thư mục + “/” đại diện cho việc bỏ qua tất cả các tập tin trong thư mục đó, “*” + phần mở rộng tên tập tin đại diện cho việc bỏ qua tất cả các tập tin có phần mở rộng đó.

.vscode/  : Đây là thư mục cấu hình của VS Code.

Cache/  : Đây là thư mục chứa các tập tin cache.

Libraries/ : Đây là thư mục chứa các thư viện chính thức không thể chỉnh sửa.

Temp/ : Đây là thư mục tạm thời, chứa các nội dung như nhật ký chạy.

*.lock : Đây là tất cả các tập tin bị khóa.

Trên đây là các tập tin được Git khuyến nghị bỏ qua.

## Quy tắc chỉnh sửa tập tin .gitignore

Thông thường, bạn không cần chỉnh sửa tập tin `.gitignore`. Tuy nhiên, nếu bạn có thêm các tập tin cần bỏ qua hoặc muốn thêm các tập tin để theo dõi, bạn có thể tham khảo hướng dẫn này. Tuy nhiên, cần lưu ý rằng tập tin `.gitignore` cần được đồng bộ hóa với kho từ xa, và tất cả các cộng tác viên trong kho sẽ bị ảnh hưởng bởi các thay đổi cấu hình của tập tin này.

### Chú thích

Các dòng bắt đầu bằng `#` là chú thích.

![image-20240724160110626](./img/image-20240724160110626.png)

### Bỏ qua tập tin và thư mục

Nhập một chuỗi ký tự sẽ bỏ qua các thư mục và tập tin có cùng tên:

![image-20240724160343666](./img/image-20240724160343666.png)

> Tuy nhiên, thường thì tập tin sẽ có phần mở rộng để phân biệt với tên thư mục.

### Bỏ qua chỉ thư mục

![image-20240724160709884](./img/image-20240724160709884.png)

Bỏ qua tất cả các tập tin trong thư mục có tên đó. Bao gồm các thư mục cùng tên trong các thư mục nhiều cấp, ví dụ: */foldername/

### Sử dụng ký tự đại diện

1. Ký tự sao "*" phù hợp với nhiều ký tự. `*.test` đại diện cho việc bỏ qua tất cả các tập tin kết thúc bằng `.test`.
2. Ký tự hỏi "?" phù hợp với bất kỳ ký tự nào ngoài "/" một lần. `t?st` đại diện cho việc bỏ qua tất cả các tập tin hoặc thư mục có tên gồm bốn ký tự, với các ký tự thứ 1, 3 và 4 là `t`, `s`, `t`.

3. Dấu ngoặc vuông "[]" phù hợp với mỗi ký tự trong dấu ngoặc vuông. `*.[abc]` đại diện cho tất cả các tập tin kết thúc bằng `.a`, `.b`, hoặc `.c`.

   Sử dụng dấu gạch ngang trong dấu ngoặc vuông để phù hợp với phạm vi các ký tự, `[0-9]` đại diện cho việc lần lượt phù hợp với các số từ 0 đến 9.

### Hoạt động ngược

Sử dụng "!" có thể thêm các tập tin đã bị bỏ qua trước đó vào danh sách theo dõi.

![image-20240724161929601](./img/image-20240724161929601.png)

> Tập tin `filename` trong thư mục `foldername` sẽ được theo dõi lại.

### Các quy tắc khác

1. Mỗi dòng trong tập tin `.gitignore` là một mẫu phù hợp, dòng trống không phù hợp với bất kỳ tập tin nào.
2. Git theo dõi tập tin, không phải thư mục.
3. Nếu tập tin đã được Git theo dõi, thì ngay cả khi thêm vào tập tin `.gitignore` cũng sẽ không bị bỏ qua.

Nếu bạn có nhu cầu thêm, bạn có thể tự tham khảo hướng dẫn sử dụng gitignore và Git.
```