# Goal  
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

# Các bước thực hiện
1. Đăng nhập vào bandit8
2. ls -> data.txt
3. Sử dụng lệnh
   ```bash
   sort data.txt | uniq -u
   ```
-> Tìm thấy mật khẩu:
```bash
EjmOSvuAu7sGAHqHVcBDPirRe9T03kxl
```

**sort data.txt:** Sắp xếp các dòng trong tệp theo thứ tự bảng chữ cái. Bước này bắt buộc vì lệnh `uniq` chỉ so sánh được các dòng đứng liền kề nhau
**| (Pipe):** Truyền dữ liệu đã được sắp xếp từ lệnh `sort` sang làm đầu vào cho lệnh `uniq`
**uniq -u:** Tham số `-u` (--unique) lọc và chỉ hiển thị dòng duy nhất xuất hiện đúng một lần

# Lệnh Sort
**Lệnh Sort** sắp xếp các dòng dữ liệu trong tệp tin hoặc luồng đầu vào theo thứ tự alphabet hoặc giá trị số.  
**Cơ chế:** Mắc định: `sort` đọc dữ liệu và so sánh từng ký tự từ trái sang phải theo bảng mã ASCII để sắp xếp theo thứ tự tăng dần (A-Z, 0-9)
**Các tùy chọn (flags) phổ biến:**
`-n` (--numeric-sort): Sắp xếp theo giá trị số thực tế. Nếu không có tùy chọn này, số `100` sẽ đứng trước số `2` vì ký tự `1` nhỏ hơn `2`.  
`-r` (--reverse): Đảo ngược thứ tự sắp xếp (từ Z về A, từ lớn đến nhỏ)  
`-k` (--key): Chọn cột (field) làm căn cứ sắp xếp. Ví dụ: `-k 2` sẽ sắp xếp theo nội dung cột thứ 2  
`-t` (--field-separator): Chỉ định ký tự phân cách các cột (mặc định là khoảng trắng hoặc tab).  

# Lệnh `uniq`
**Lệnh uniq** kiểm tra dữ liệu văn bản để lọc bỏ, đếm hoặc chỉ hiển thị các dòng lặp lại.  
**Cơ chế:** `uniq` so sán dòng hiện tại với dòng liền kề ngay phía trước. Nếu hai dòng giống hệt nhau không nằm kế tiệp nhau, `uniq` sẽ không phát hiện sự trùng lặp  
**Các tùy chọn (flags) phổ biến:**  
`-c` (--count): đếm số lần xuất hiện của tùng dòng và in số đếm đó ở đầu dòng

`-u` (--unique): chỉ in ra những dòng xuất hiện đúng 1 lần duy nhất

`-d` (--repeated): chỉ in ra những dòng bị lặp lại (xuất hiện từ 2 lần trở lên)  

`-i` (--ignore-case): Bỏ qua phân biết chữ hoa và chữ thường khi so sánh


