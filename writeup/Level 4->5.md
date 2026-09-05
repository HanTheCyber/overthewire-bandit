# Goal
The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

# Các bước thực hiện
1. Đăng nhập vào bandit4
2. `ls` -> `inhere`
3. `cd inhere`
4. `la -la` -> hiển thị danh sách chi tiết tất cả các tệp và thư mục (bao gồm cả tệp ẩn) trong thư mục hiện tại `inhere`
<img width="590" height="311" alt="Screenshot from 2026-09-05 05-06-02" src="https://github.com/user-attachments/assets/42c8e833-0bdd-469c-9983-0e8fd3d6d25a" />

5.`file ./-*` -> kiểm tra và trả về định dạng dữ liệu thực sự của tất cả các tệp trong thư mục hiện tại  
<img width="630" height="246" alt="Screenshot from 2026-09-05 05-36-56" src="https://github.com/user-attachments/assets/0e933b2b-2a9b-42b2-aa22-825c068fd99f" />

-> Trong danh sách kết quả trả về, hầu hết các tệp là data (dữ liệu nhị phân/rác), ngoại trừ một tệp duy nhất có dạng ASCII text. Đó chính là tệp chứa mật khẩu.

6. cat ./-file07 -> Tìm được mật khẩu:
   ```bash
   6C7h9GD8M6ai5nr7wo1RonrzFjj9yIrG
   ```
