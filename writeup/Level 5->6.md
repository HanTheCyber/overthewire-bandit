# Goal
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:
    human-readable
    1033 bytes in size
    not executable

# Các bước thực hiện
1. Đăng nhập vào bandit5
2. ls -> inhere
3. cd inhere
4. ls -la -> file maybe*

<img width="598" height="470" alt="Screenshot from 2026-09-05 06-10-44" src="https://github.com/user-attachments/assets/6a685ce5-212c-4cf9-8722-26c723cbcba2" />

<img width="598" height="558" alt="Screenshot from 2026-09-05 06-10-28" src="https://github.com/user-attachments/assets/224e400b-47cf-4d47-a6c3-9d3fd685a4d3" />

-> trong thư viện `inhere`, số lượng tệp lên tới hàng trăm. Vì thế không thể kiểm tra thủ công hay dùng lệnh đơn giản như file được nữa, mà bắt buộc phải dùng lệnh find kết hợp nhiều điều kiện lọc (kích thước 1033c, quyền đọc -readable, loại trừ file thực thi ! -executable).

5. Sử dụng lệnh
```bash
find . -type f -readable -size 1033c ! -executable
```

6. Tìm được mật khẩu
```bash
pXa26xhMWaC2SvDotA4r9EgZkulOeSBW
```

# Về `find`  
Lệnh find trong Linux/Unix dùng để tìm kiếm tệp (files) và thư mục (directories) theo các tiêu chí cụ thể dựa trên cấu trúc cây thư mục.
## 1. Công dụng chính
Tìm theo tên: Tìm tệp/thư mục có tên chính xác hoặc chứa từ khóa.
Tìm theo kích thước: Lọc tệp có dung lượng nhỏ hơn, lớn hơn hoặc đúng bằng một số byte/KB/MB cụ thể.
Tìm theo loại (type): Phân loại chỉ tìm tệp thường (f), thư mục (d), hay liên kết (l).
Tìm theo quyền (permissions): Tìm các tệp có quyền đọc, ghi, hoặc thực thi nhất định (-readable, -executable, -perm).
Tìm theo thời gian: Tìm tệp được tạo, sửa đổi hoặc truy cập trong khoảng thời gian nhất định (-mtime, -atime).
Thực thi lệnh trực tiếp: Tự động thực hiện một hành động (như xóa, di chuyển, đổi tên) lên các tệp vừa tìm thấy thông qua tham số -exec.
## 2. Cú pháp cơ bản
```bash
find <vị-trí-tìm-kiếm> <tiêu-chí-lọc>
```
## 3. Các lệnh cơ bản
-Tìm tệp theo tên
```bash
find . -name "test.txt"
```
-Tìm tất cả tệp có đuôi .log:
```bash
find /var/log -name "*.log"
```
-Tìm tệp có dung lượng lớn hơn 100MB:
```bash
find / -size +100M
```
-Tìm và xóa tất cả các tệp tạm .tmp:
```bash
find . -name "*.tmp" -delete
```
