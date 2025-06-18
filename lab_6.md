# Bài Lab 06: Mảng và Lớp ArrayList

- **Môn học:** Lập trình Hướng đối tượng
- **Thời gian:** 120 phút
- **Mục tiêu:**
  - Củng cố kiến thức về mảng một chiều và đa chiều.
  - Vận dụng các thuật toán cơ bản trên mảng: tìm kiếm tuần tự, tìm kiếm nhị phân, sắp xếp chọn.
  - Hiểu và sử dụng mảng song song (parallel arrays) để quản lý dữ liệu liên quan.
  - Biết cách nhận và xử lý tham số dòng lệnh (command-line arguments).
  - Làm quen và sử dụng lớp `ArrayList` cho các tác vụ lưu trữ động.

---

## Yêu cầu chung

- Tạo một project Java mới trong IDE của bạn.
- Mỗi bài tập sẽ được thực hiện trong một class riêng biệt (ví dụ: `Bai1.java`, `Bai2.java`...).
- Viết các phương thức tĩnh (static) để xử lý các thuật toán, giúp mã nguồn rõ ràng và dễ tái sử dụng.
- Đọc kỹ đề bài và các yêu cầu, gợi ý trước khi bắt đầu code.

---

### **Bài 1: Thuật toán trên Mảng một chiều (Thời gian dự kiến: 45 phút)**

**Mục tiêu:** Luyện tập triển khai các thuật toán tìm kiếm và sắp xếp cơ bản.

**Yêu cầu:**

1.  Tạo một class `Bai1`.
2.  Trong `main`, khởi tạo một mảng số nguyên `int[] arr` với các giá trị cho trước (không cần nhập từ bàn phím). Ví dụ: `int[] arr = {15, 8, 23, 1, 9, 17, 5, 12};`.
3.  **Tìm kiếm tuần tự (Sequential Search):**
    -   Viết một phương thức tĩnh `timKiemTuanTu(int[] array, int value)` nhận vào một mảng và một giá trị cần tìm.
    -   Phương thức trả về chỉ số (index) đầu tiên của `value` trong `array`. Nếu không tìm thấy, trả về `-1`.
4.  **Sắp xếp chọn (Selection Sort):**
    -   Viết một phương thức tĩnh `sapXepChon(int[] array)` nhận vào một mảng và sắp xếp các phần tử của mảng đó theo thứ tự tăng dần. Phương thức này không trả về giá trị (`void`), nó sẽ thay đổi trực tiếp trên mảng được truyền vào.
5.  **Tìm kiếm nhị phân (Binary Search):**
    -   Viết một phương thức tĩnh `timKiemNhiPhan(int[] array, int value)` nhận vào một mảng **đã được sắp xếp** và một giá trị cần tìm.
    -   Phương thức trả về chỉ số của `value` trong `array`. Nếu không tìm thấy, trả về `-1`.
6.  Trong phương thức `main`:
    -   Gọi `timKiemTuanTu` để tìm một phần tử có trong mảng và một phần tử không có. In kết quả.
    -   Gọi `sapXepChon` để sắp xếp mảng. In mảng sau khi sắp xếp.
    -   Gọi `timKiemNhiPhan` trên mảng **đã sắp xếp** để tìm một phần tử. In kết quả.

**Gợi ý:**

-   Để in mảng, bạn có thể dùng `Arrays.toString(arr)`.
-   Nhớ rằng tìm kiếm nhị phân chỉ hoạt động chính xác trên mảng đã được sắp xếp.

---

### **Bài 2: Mảng Song song và Mảng Hai chiều (Thời gian dự kiến: 40 phút)**

**Mục tiêu:** Vận dụng mảng song song và mảng hai chiều để quản lý một tập dữ liệu phức tạp hơn.

**Yêu cầu:**

1.  Tạo một class `Bai2`.
2.  **Mảng song song (Parallel Arrays):**
    -   Trong `main`, tạo 2 mảng song song:
        -   `String[] danhSachTen = {"An", "Bình", "Châu", "Dũng", "Giang"};`
        -   `double[] danhSachDiem = {8.5, 7.0, 9.2, 5.5, 6.8};`
    -   Viết một phương thức tĩnh `hienThiDiem(String[] ten, double[] diem, String tenSV)` nhận vào 2 mảng song song và tên một sinh viên.
    -   Phương thức sẽ tìm tên sinh viên trong mảng `ten`, và nếu tìm thấy, sẽ in ra màn hình tên và điểm tương ứng ở mảng `diem`. Nếu không tìm thấy, thông báo "Không tìm thấy sinh viên".
3.  **Mảng hai chiều (Two-Dimensional Arrays):**
    -   Trong `main`, tạo một mảng hai chiều `double[][] bangDiem` để lưu điểm 3 môn (Toán, Lý, Hóa) của 3 sinh viên.
        ```java
        double[][] bangDiem = {
            {7.5, 8.0, 8.5}, // Điểm của SV 1
            {6.0, 7.5, 6.5}, // Điểm của SV 2
            {9.0, 9.5, 10.0} // Điểm của SV 3
        };
        ```
    -   Viết một phương thức tĩnh `tinhDiemTrungBinh(double[][] bangDiem, int maSV)` nhận vào bảng điểm và mã sinh viên (là chỉ số của hàng, ví dụ: 0, 1, 2).
    -   Phương thức này tính và trả về điểm trung bình của sinh viên đó.
4.  Trong phương thức `main`:
    -   Gọi `hienThiDiem` để tìm điểm của "Châu" và "Hùng".
    -   Sử dụng vòng lặp để gọi `tinhDiemTrungBinh` cho từng sinh viên (từ 0 đến 2) và in điểm trung bình của họ ra màn hình.

**Lưu ý về Mảng Ba chiều:** Mảng 3 chiều có thể được hình dung như một khối lập phương dữ liệu, ví dụ: `diem[lop][sinhVien][monHoc]`. Cách truy cập và duyệt tương tự như mảng 2 chiều nhưng thêm một cấp độ lồng nhau nữa.

---

### **Bài 3: `ArrayList` và Tham số Dòng lệnh (Thời gian dự kiến: 35 phút)**

**Mục tiêu:** Tìm hiểu sự linh hoạt của `ArrayList` và cách nhận dữ liệu từ dòng lệnh khi chạy chương trình.

**Yêu cầu:**

1.  Tạo một class `Bai3`.
2.  Chương trình này sẽ nhận một danh sách các tên sản phẩm từ tham số dòng lệnh và quản lý chúng bằng `ArrayList`.
3.  Trong phương thức `main(String[] args)`:
    -   Tạo một `ArrayList<String>` có tên là `gioHang`.
    -   Dùng vòng lặp `for` để duyệt qua mảng `args`. Với mỗi phần tử trong `args`, hãy thêm nó vào `gioHang` bằng phương thức `.add()`.
    -   In ra danh sách các sản phẩm trong giỏ hàng và số lượng sản phẩm.
    -   Thực hiện các thao tác sau trên `ArrayList`:
        -   Kiểm tra xem "Bim bim" có trong giỏ hàng không. In kết quả.
        -   Xóa sản phẩm ở chỉ số 0 (nếu có).
        -   Xóa sản phẩm có tên là "Sữa" (nếu có).
    -   In lại danh sách sản phẩm cuối cùng trong giỏ hàng.

**Cách chạy chương trình với tham số dòng lệnh:**

1.  **Biên dịch file Java:** Mở Terminal hoặc Command Prompt, di chuyển đến thư mục chứa file `Bai3.java` và chạy lệnh:
    ```bash
    javac Bai3.java
    ```
2.  **Chạy file đã biên dịch và truyền tham số:**
    ```bash
    java Bai3 "Bánh mì" Sữa "Kẹo mút" "Bim bim"
    ```
    -   `"Bánh mì"`, `Sữa`, `"Kẹo mút"`, `"Bim bim"` chính là các phần tử của mảng `args`.
    -   Các chuỗi có khoảng trắng cần được đặt trong dấu ngoặc kép.

**Ví dụ output mong muốn:**

```
Danh sách sản phẩm ban đầu: [Bánh mì, Sữa, Kẹo mút, Bim bim]
Số lượng sản phẩm: 4

Giỏ hàng có chứa "Bim bim": true

Danh sách sản phẩm sau khi xóa: [Kẹo mút, Bim bim]
```
