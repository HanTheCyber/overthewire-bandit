## Level 1 -> Level 2:
### 1. Mục tiêu:
Tìm mật khẩu của `bandit2` được lưu trong file`-` ở thư mục home
### 2. Các bước thực hiện:  
-Kết nối ssh vào `bandit1`:  
```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
# Password: 6y2kwnwK6grgvwvpvLaa2T1cpFEKOhNR
```
-Kiểm tra danh sách file trong thư viện home:
```bash
ls
# Kết quả hiển thị file tên là '-'
```
-Đọc nội dung file '-':  
```bash
cat ./-
```
-Tìm thấy mật khẩu:
```bash
PK8fYLZg2hnHSz83plBL1iEPKdD3QToB
```

Nếu chỉ gõ `cat -`, Linux sẽ hiểu dấu `-` là đọc từ đầu vào tiêu chuẩn (stdin) chứ không phải tên file. Nêu dùng ./- để chỉ định rõ đường dẫn tương đối đến file `-` trong thư mục hiện tại.
