# Bài Lab 03: Lập Trình Với Phương Thức (Methods) trong Java

- **Môn học:** Lập trình Hướng đối tượng
- **Thời gian:** 120 phút
- **Mục tiêu:**
  - Hiểu và định nghĩa được các phương thức đơn giản (void methods).
  - Biết cách truyền tham số cho phương thức (Passing Arguments).
  - Hiểu về phạm vi của biến cục bộ (Local Variables).
  - Biết cách sử dụng và trả về giá trị từ một phương thức (Returning a Value).
  - Áp dụng phương thức để chia nhỏ và giải quyết các bài toán phức tạp (Problem Solving).

---

## Yêu cầu chung

- Tạo một project Java mới trong IDE của bạn (IntelliJ, Eclipse, NetBeans...).
- Mỗi bài tập sẽ được thực hiện trong một class riêng biệt (ví dụ: `Bai1.java`, `Bai2.java`...).
- Các phương thức xử lý logic (phương thức con) không nên chứa code để nhập/xuất dữ liệu, trừ khi đề bài yêu cầu cụ thể. Việc nhập/xuất nên được thực hiện trong phương thức `main`.
- Đọc kỹ đề bài và các yêu cầu, gợi ý trước khi bắt đầu code.

---

### **Bài 1: Vẽ hình chữ nhật (Thời gian dự kiến: 20 phút)**

**Mục tiêu:** Luyện tập tạo phương thức không trả về giá trị (void) và truyền tham số.

**Yêu cầu:**

1.  Tạo một class tên là `Bai1`.
2.  Trong class `Bai1`, viết một phương thức tĩnh (static) tên là `veHinhChuNhat` nhận vào 2 tham số là số nguyên `chieuDai` và `chieuRong`.
3.  Phương thức này sẽ có nhiệm vụ in ra màn hình một hình chữ nhật rỗng bằng các dấu `*` có kích thước tương ứng.
4.  Trong phương thức `main`, gọi phương thức `veHinhChuNhat` với ít nhất 2 bộ giá trị khác nhau để kiểm tra (ví dụ: `(10, 5)` và `(20, 7)`).

**Ví dụ output khi gọi `veHinhChuNhat(10, 5)`:**

```
**********
*        *
*        *
*        *
**********
```

**Gợi ý:**

-   Sử dụng 2 vòng lặp `for` lồng nhau.
-   Dùng câu lệnh `if-else` để kiểm tra xem vị trí hiện tại có phải là ở cạnh của hình chữ nhật hay không để in ra `*` hoặc khoảng trắng ` `.
-   Vị trí ở cạnh khi:
    -   Hàng đầu tiên hoặc hàng cuối cùng (`i == 0 || i == chieuRong - 1`).
    -   Cột đầu tiên hoặc cột cuối cùng (`j == 0 || j == chieuDai - 1`).

---

### **Bài 2: Máy tính đơn giản (Thời gian dự kiến: 45 phút)**

**Mục tiêu:** Luyện tập viết phương thức có trả về giá trị và xử lý logic cơ bản.

**Yêu cầu:**

1.  Tạo một class tên là `Bai2`.
2.  Viết các phương thức tĩnh (static) sau, mỗi phương thức nhận vào 2 tham số kiểu `double` và trả về kết quả tương ứng:
    -   `tinhTong(double a, double b)`: trả về tổng `a + b`.
    -   `tinhHieu(double a, double b)`: trả về hiệu `a - b`.
    -   `tinhTich(double a, double b)`: trả về tích `a * b`.
    -   `tinhThuong(double a, double b)`: trả về thương `a / b`.
3.  Trong phương thức `main`, thực hiện các công việc sau:
    -   Hiển thị một menu cho người dùng lựa chọn phép toán:
        ```
        +-----------------------------------+
        |          MÁY TÍNH ĐƠN GIẢN        |
        +-----------------------------------+
        | 1. Cộng                          |
        | 2. Trừ                            |
        | 3. Nhân                           |
        | 4. Chia                           |
        | 0. Thoát                          |
        +-----------------------------------+
        Chọn chức năng:
        ```
    -   Sử dụng vòng lặp `do-while` hoặc `while` để chương trình chạy lặp lại cho đến khi người dùng chọn `0` để thoát.
    -   Yêu cầu người dùng nhập vào 2 số thực `a` và `b`.
    -   Sử dụng cấu trúc `switch-case` để gọi phương thức tương ứng với lựa chọn của người dùng.
    -   In kết quả của phép toán ra màn hình.
    -   **Lưu ý:** Đối với phép chia, hãy kiểm tra nếu `b` bằng 0 thì thông báo lỗi "Không thể chia cho 0!" thay vì thực hiện phép chia.

**Gợi ý:**

-   Sử dụng lớp `Scanner` để nhận dữ liệu nhập từ bàn phím.
-   Các biến để lưu lựa chọn của người dùng, hai số `a` và `b` là các **biến cục bộ** (local variables) trong phương thức `main`.
-   Kết quả trả về từ các phương thức tính toán nên được gán vào một biến cục bộ trong `main` trước khi in ra màn hình.

---

### **Bài 3: Tiện ích với số nguyên tố (Thời gian dự kiến: 55 phút)**

**Mục tiêu:** Vận dụng các kiến thức về phương thức để giải quyết một bài toán có cấu trúc, chia nhỏ vấn đề thành các hàm con.

**Yêu cầu:**

1.  Tạo một class tên là `Bai3`.
2.  Trong class `Bai3`, viết phương thức tĩnh `laSoNguyenTo(int n)`.
    -   Phương thức này nhận vào một số nguyên `n`.
    -   Trả về `true` nếu `n` là số nguyên tố, ngược lại trả về `false`.
    -   **Định nghĩa số nguyên tố:** Là số tự nhiên lớn hơn 1 và chỉ có hai ước là 1 và chính nó. Số 2 là số nguyên tố duy nhất là số chẵn.
3.  Trong class `Bai3`, viết một phương thức tĩnh khác `lietKeSoNguyenTo(int gioiHan)`.
    -   Phương thức này nhận vào một số nguyên `gioiHan` là giới hạn trên.
    -   Phương thức này sẽ in ra màn hình tất cả các số nguyên tố từ 2 cho đến `gioiHan`.
    -   Để thực hiện việc này, phương thức `lietKeSoNguyenTo` phải gọi lại phương thức `laSoNguyenTo` đã viết ở trên để kiểm tra từng số.
4.  Trong phương thức `main`:
    -   Yêu cầu người dùng nhập vào một số nguyên dương `N`.
    -   Gọi phương thức `lietKeSoNguyenTo(N)` để in ra danh sách các số nguyên tố nhỏ hơn hoặc bằng `N`.

**Ví dụ output khi người dùng nhập `N = 20`:**

```
Nhập vào giới hạn N: 20
Các số nguyên tố từ 2 đến 20 là:
2 3 5 7 11 13 17 19
```

**Gợi ý cho phương thức `laSoNguyenTo(int n)`:**

-   Nếu `n < 2`, chắc chắn không phải là số nguyên tố.
-   Sử dụng một vòng lặp `for` chạy từ `2` đến `sqrt(n)` (căn bậc hai của `n`). Nếu `n` chia hết cho bất kỳ số nào trong khoảng này, nó không phải là số nguyên tố.
-   Để tính căn bậc hai, bạn có thể dùng `Math.sqrt(n)`.
-   Phương thức này là một ví dụ điển hình của việc **trả về một giá trị boolean** để biểu thị một trạng thái (Đúng/Sai). Việc **chia nhỏ bài toán** "Liệt kê các số nguyên tố" thành "Kiểm tra một số có phải nguyên tố không" là cốt lõi của bài tập này.
