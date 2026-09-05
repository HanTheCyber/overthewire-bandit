# Goal
The password for the next level is stored somewhere on the server and has all of the following properties:  
owned by user bandit7  
owned by group bandit6  
33 bytes in size

# Các bước thực hiên
1. Đăng nhập vào bandit5
2. Sử dụng lệnh find bắt đầu từ thư mục gốc / kết hợp lọc theo các tiêu chí đã cho. Tuy nhiên, nếu chỉ dùng lệnh `find / -user bandit7 -group bandit6 -size 33c` thì nhiều file sẽ bị báo lỗi "Permission denied" (không đủ quyền truy cập), do tài khoản bandit6 chỉ là một người dùng thường (không phải quyền root), hệ thống sẽ từ chối quyền đọc ở những thư mục bảo mật hoặc thuộc về người dùng khác. Tệp kết quả thực sự bạn cần tìm đang bị "trôi" hoặc lẫn lộn giữa hàng trăm dòng thông báo lỗi này.
 <img width="865" height="669" alt="Screenshot from 2026-09-05 08-19-53" src="https://github.com/user-attachments/assets/99853601-4bc4-4ce7-98a5-a6ea57c4a08b" />

 -> Sử dụng lệnh
   ```bash
   find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
   ```

Kết quả: /var/lib/dpkg/info/bandit7.password  

3. `cat /var/lib/dpkg/info/bandit7.password`  
-> Tìm thấy mật khẩu:
```bash
Bmnnvf82KzQlfxgAI2d1zYbr1u9pr3E3
```
