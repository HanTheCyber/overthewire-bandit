# Goal
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.  

# Các bước thực hiện
1. Đăng nhập vào bandit9
2. Nếu chỉ sử dụng lệnh `grep "="` thì sẽ bị lỗi
   <img width="371" height="48" alt="Screenshot from 2026-09-08 14-54-57" src="https://github.com/user-attachments/assets/bb78ce63-f582-44a5-bbbd-8a3dc152fa60" />

   vì tệp `data.txt` chứa dữ liệu nhị phân (binary). Lệnh `grep` khi gặp dữ liệu nhị phân sẽ tự động chặn hiển thị nội dung chi tiết ra màn hình để tránh làm hỏng hoặc vỡ giao diện Terminal.
Do đó, ta cần kết hợp lệnh `string` với `grep`, dùng lệnh strings để chuyển toàn bộ ký tự nị phân tành văn bản đọc được trước, sau đó mới truyền qua lệnh grep
```bash
strings data.txt | grep "="
```
**strings data.txt:** Trích xuất toàn bộ chuỗi văn bản đọc được từ tệp tin dữ liệu thô/ nhị phân  
**grep "=":** Lọc ra các dingf có chứa ký tự `=`.  
<img width="548" height="318" alt="Screenshot from 2026-09-08 15-06-30" src="https://github.com/user-attachments/assets/c346b665-b8c8-4e0f-86af-174c211ce400" />
-> Tìm được mật khẩu:
```bash
B0s2khmbT9u0geKuOoVGW3JZKhndE3BG
```
