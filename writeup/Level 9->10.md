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

# Lệnh strings
**Lệnh strings** là công cụ trong Linux/Unix chuyên dùng để tìm và trích xuất tất cả các chuỗi ký tự đọc được (printable characters) từ một tệp tin, đặc biệt hữu ích với các tệp nhị phân (binary), file thực thi, hoặc file dữ liệu thô.  
**Cách hoạt động chi tiết**

1. Quét dữ liệu dạng Byte: strings mở tệp tin và đọc từng byte từ đầu đến cuối

2. Lọc ký tự in được: Lệnh lọc ra các ký tự nằm trong bảng mac ASCII hiển thị được (chữ cái a-z, A-Z, chữ số 0-9, các dấu câu và khoảng trắng)

3. Độ dài tối thiểu: Mặc định, strings chỉ in ra các chuỗi có từ 4 ký tự liên tiếp trở lên và kết thúc bằng một ký tự ngắt (như ký tự rỗng \0 hoặc xuống dòng \n). Tất cả các đoạn mã máy nhị phân không đọc được giữa các chuỗi này sẽ bị loại bỏ

**Các tùy chọn (Flags) phổ biến:**

`-n <số_lượng>` (hoặc gõ tắt -[số-lượng]): thay đổi độ dài tối thiểu của chuỗi cần lấy (mặc định là 4)

`-t <định_dạng>`: Hiển thị vị trí (offset) của chuỗi bên trong tệp tin
      
      `-t d`: Vị trí dạng Thập phân (Decimal)
      
      `-t x`: Vị trí dạng Thập lục (Hexadecimal)
      
      `-t o`: Vị trí dạng Bát phân (Octal)
   
`-e <kiểu_mã_hóa>`: Chỉ định kiểu mã hóa ký tự để tìm kiếm (mặc định là 7-bit ASCII)
      
      `s` = 7-bit ASCII
      
      `b` = 16-bit big-endian (Unicode)
      
      `l` =16-bit little-endian
   
