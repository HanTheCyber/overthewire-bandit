# Goal
The password for the next level is stored in the file `data.txt` next to the word `millionth`

# Các bước thực hiện
1. Đăng nhập vào bandit7
2. ls -> data.txt
3. grep millionth data.txt
   -> Tìm được mật khẩu:
   ```bash
   VR1ljMayciFxbnUokuQmJFw6QC9VKtub
   ```
# Lệnh Grep:
Lệnh Grep là một công cụ dòng lệnh trên Linux/Unix dùng để tìm kiếm các chuỗi ký tự hoặc mô hình (pattern) trong tệp tin hoặc luồng dữ liệu đầu vào

**Cú pháp cơ bản:**
```bash
grep [tùy_chọn] "mẫu_tìm_kiếm" [tệp_ tin]
```
**tùy_chọn (options):** Các tham số điều chỉnh hành vi tìm kiếm (như phân biệt hoa/thường, đếm số dòng, tìm trong thư mục con...)
**mẫu_tìm_kiếm (pattern):** Chuỗi văn bản cố định hoặc biểu thức chính quy (Regular Expression - Regex)
**tệp_tin:** Tệp tin cần quét dữ liệu. Nếu không chỉ định tệp, grep sẽ đọc dữ liệu từ đầu vào chuẩn (Standard Input - stdin) thông qua đường ống (pipe |)

**Cách hoạt động chi tiết:**
1. Đọc dữ liệu theo dòng: grep mở tệp tin hoặc tiếp nhận luồng dữ liệu từ lệnh khác, sau đó chia nhỏ dữ liệu thành từng dòng riêng biệt bằng ký tự ngắt dòng (\n)
2. Khớp mô hình (Pattern Matching): với mỗi dòng đọc được, trình biểu thức chính quy (Regex Engine) của grep sẽ kiểm tra xem chuỗi mẫu có xuất hiện trong dòng đó hay không
3. In kết quả: Nếu tìm thấy kết quả khớp, grep sẽ chuyển toàn bộ dòng chứa chuỗi đó ra đầu ra chuẩn (Standard Output - stdout) để hiển thị lên màn hình. Dòng không chứa chuỗi khớp sẽ bị bỏ qua

