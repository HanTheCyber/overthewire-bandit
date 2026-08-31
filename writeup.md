# OverTheWire: Bandit Write-up

## Level 0 -> Level 1
### 1. Mục tiêu
Tìm mật khẩu của `bandit1` được lưu trong file `readme` ở thư mục home.
### 2. Các bước thực hiện:
-Kết nối SSH vào `bandit0`:
```bash
   ssh bandit0@bandit.labs.overthewire.org -p 2220
# Password: bandit0
```
-Kiểm tra danh sách file trong thư mục home:  
```bash
ls
# Kết quả hiển thị file tên là 'readme'
```
-Đọc nội dung file 'readme'  
```bash
cat readme
```
-Tìm thấy mật khẩu: 
```bash 
6y2kwnwK6grgvwvpvLaa2T1cpFEKOhNR
```


