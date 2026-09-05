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
