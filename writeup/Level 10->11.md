# Goal
The password for the next level is stored in the file data.txt, which contains base64 encoded data

# Các bước thực hiện:
1. Đăng nhập vào bandit10
2. Sử dụng lệnh `ls -l` để kiểm tra sự tồn tại của file data.txt
3. Ta có thể kiểm tra dữ liệu trong tệp data.txt bằng lệnh `cat data.txt` -> Nhìn thấy một chuỗi các lệnh kết thúc bằng dấu "=" (hoặc "=="), đây chính là đặc trưng của chuỗi đã được mã hóa bằng `Base64`
4. Giải mã `Base64` tìm mật khẩu:
   Linux có sẵn công cụ `base64`. Sử dụng tùy chọn `-d` (hoặc `--decode`) để giải mã nội dung tệp `data.txt`:
   ```bash
   base64 -d data.txt
   ```
   hoặc sử dụng pipe `|`
   ```bash
   cat data.txt | base64 -d
   ```
   -> Tìm thấy mật khẩu:
   ```bash
   pYfOY6HwUsDj5rL9UvyhU7MCmv8vN5Ro
   ```

# Lệnh `base64`
Là một công cụ dùng để `mã hóa (encode)` hoặc `giải mã (decode)` dữ liệu sang định dạng chuẩn Base64
**Mã hóa Base64 là gì?** Là kỹ thuật chuyển đổi dữ liệu nhị phân (binary) hoặc văn bản thành một chuỗi ký tự chỉ bao gồm 64 ký tự an toàn trong bản mã ASCII (bao gồm: A-Z, a-z, 0-9, dấu +,/, và dùng dấu = để làm ký tự đệm/padding ở cuối).  
**Mục đích sử dụng**
**-Truyền tải dữ liệu an toàn trên mạng** Giúp truyền dữ liệu nhị phân (như hình ảnh, tệp tin, chứng chỉ SSL) qua các hệ thống chỉ hỗ trợ văn bản (như Email, HPPT, JSON/XML) mà không lo bị lỗi định dạng.  
**-Đơn giản hóa dữ liệu trong lập trình & CFT** Thường dùng để đóng gói chuỗi dữ liệu hoặc che giấu thông tin cơ bản (dù Base64 không phải là phương pháp bảo mật hay mã hóa an toàn vì ai cũng có thể giải mã được).  
**Cú pháp và cách dùng phổ biến**
`Mã hóa (Encode)`
Mã hóa một chuỗi văn bản:  
```bash
echo "Hello World" | base64
```
Mã hóa một tệp tin
```bash
base64 file.txt
```
`Giải mã (Decode)`
Chuyển chuỗi Base64 trở lại văn bản ban đầu (dùng tùy chọn `-d` hoặc `--decode`):  
Giải mã chuỗi văn bản Base64
```bash
echo "SGVsbG8gV29ybGQK" | base64 -d
```
Giải mã từ một tệp tin chữa mã Base64  
```bash
base64 -d encoded_file.txt
```


# Tùy chọn -d
   Là viết tắt của --decode (giải mã). Không có -d: Lệnh base64 sẽ đóng vai trò là người mã hóa (biến chuỗi văn bản/tệp tin bình thường thành dạng mã Base64). Có -d: Lệnh base64 đổi sang chế độ giải mã (biến chuỗi Base64 trở lại dạng văn bản ban đầu).

   #Tóm tắt lệnh cần nhớ:
   `base64 <file>`: Mã hóa nội dung tệp sang dạng Base64.
   `base64 -d <file>` hoặc `base64 --decode <file>`: Giải mã dữ liệu từ Base64 về dạng văn bản gốc (plaintext).
