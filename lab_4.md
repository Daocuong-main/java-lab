# Bài Lab 04: Giới thiệu về Lớp và Đối tượng (Classes and Objects)

- **Môn học:** Lập trình Hướng đối tượng
- **Thời gian:** 120 phút
- **Mục tiêu:**
  - Hiểu khái niệm về Lớp (Class) và Đối tượng (Object).
  - Biết cách viết một lớp đơn giản, khai báo các trường dữ liệu (instance fields) và phương thức (methods).
  - Hiểu và sử dụng phương thức khởi tạo (Constructors), bao gồm cả việc nạp chồng (Overloading).
  - Biết cách truyền đối tượng như một tham số cho phương thức.
  - Hiểu về phạm vi của trường dữ liệu (Scope of Instance Fields).
  - Biết cách tổ chức mã nguồn bằng gói (Packages) và sử dụng câu lệnh `import`.

---

## Yêu cầu chung

- Tạo một project Java mới trong IDE của bạn.
- Tổ chức các class vào các package theo yêu cầu của từng bài.
- Đọc kỹ yêu cầu và các gợi ý trước khi bắt đầu code.
- Hoàn thành các bài tập theo thứ tự để xây dựng một chương trình hoàn chỉnh.

---

### **Bài 1: Xây dựng lớp `SinhVien` (Thời gian dự kiến: 30 phút)**

**Mục tiêu:** Thực hành tạo một lớp cơ bản với các trường dữ liệu và phương thức.

**Yêu cầu:**

1.  Tạo một package tên là `vn.edu.lab.model`.
2.  Trong package này, tạo một class tên là `SinhVien`.
3.  Khai báo các **trường dữ liệu** (instance fields) sau cho lớp `SinhVien`. Sử dụng access modifier là `public` cho các trường ở bài này để đơn giản hóa:
    -   `maSV`: kiểu `String` (Mã sinh viên)
    -   `hoTen`: kiểu `String` (Họ và tên)
    -   `diemToan`: kiểu `double`
    -   `diemLy`: kiểu `double`
    -   `diemHoa`: kiểu `double`
4.  Viết một **phương thức** (instance method) tên là `tinhDiemTrungBinh()`:
    -   Phương thức không có tham số.
    -   Phương thức này tính và trả về điểm trung bình của 3 môn Toán, Lý, Hóa. `(diemToan + diemLy + diemHoa) / 3`.
5.  Viết một **phương thức** tên là `xepLoai()`:
    -   Phương thức không có tham số.
    -   Phương thức này gọi phương thức `tinhDiemTrungBinh()` để lấy điểm trung bình.
    -   Dựa vào điểm trung bình, phương thức trả về một chuỗi `String` xếp loại học lực như sau:
        -   `>= 9.0`: "Xuất sắc"
        -   `>= 8.0`: "Giỏi"
        -   `>= 6.5`: "Khá"
        -   `>= 5.0`: "Trung bình"
        -   `< 5.0`: "Yếu"
6.  Viết một **phương thức** `hienThiThongTin()`:
    -   Phương thức không có tham số và không trả về giá trị (`void`).
    -   Phương thức này in ra toàn bộ thông tin của sinh viên bao gồm: Mã SV, Họ tên, Điểm 3 môn, Điểm trung bình và Xếp loại.
    -   Để lấy điểm trung bình và xếp loại, hãy gọi 2 phương thức đã viết ở trên.

---

### **Bài 2: Thêm Phương thức khởi tạo (Constructors) và Nạp chồng (Overloading) (Thời gian dự kiến: 30 phút)**

**Mục tiêu:** Hiểu cách khởi tạo đối tượng bằng constructor và kỹ thuật nạp chồng.

**Yêu cầu:**

1.  Trong lớp `SinhVien` đã tạo, hãy thêm các **phương thức khởi tạo** sau:
    -   **Constructor không tham số (default constructor):** Khởi tạo một đối tượng `SinhVien` với các giá trị mặc định (ví dụ: `maSV = "000"`, `hoTen = "Chưa có tên"`, các điểm bằng `0`).
    -   **Constructor có tham số:** Nhận vào đầy đủ các thông tin `maSV`, `hoTen`, `diemToan`, `diemLy`, `diemHoa` để khởi tạo giá trị cho các trường tương ứng. Đây là một ví dụ về **nạp chồng constructor**.
2.  Tạo một package mới tên là `vn.edu.lab.main`.
3.  Trong package `vn.edu.lab.main`, tạo một class `QuanLySinhVien` với phương thức `main`.
4.  Trong phương thức `main`:
    -   Sử dụng câu lệnh `import vn.edu.lab.model.SinhVien;` để có thể sử dụng lớp `SinhVien`.
    -   Tạo 3 đối tượng sinh viên:
        -   `sv1`: Sử dụng constructor có tham số để khởi tạo với thông tin đầy đủ.
        -   `sv2`: Sử dụng constructor có tham số để khởi tạo với thông tin đầy đủ khác.
        -   `sv3`: Sử dụng constructor không tham số. Sau đó, gán giá trị trực tiếp cho từng trường dữ liệu của `sv3`.
    -   Gọi phương thức `hienThiThongTin()` của cả 3 đối tượng `sv1`, `sv2`, `sv3` để kiểm tra kết quả.

---

### **Bài 3: Xây dựng lớp quản lý và tương tác giữa các đối tượng (Thời gian dự kiến: 60 phút)**

**Mục tiêu:** Vận dụng các kiến thức đã học để xây dựng một lớp quản lý, thực hành việc truyền đối tượng làm tham số và hiểu rõ hơn về sự tương tác giữa các đối tượng.

**Yêu cầu:**

1.  Trong package `vn.edu.lab.model`, tạo một class mới tên là `LopHoc`.
2.  Lớp `LopHoc` có các trường dữ liệu sau (sử dụng access modifier `private`):
    -   `tenLop`: kiểu `String`
    -   `danhSachSV`: một mảng các đối tượng `SinhVien`. Khởi tạo với kích thước cố định, ví dụ 50. (`private SinhVien[] danhSachSV = new SinhVien[50];`)
    -   `soLuongSVHienTai`: kiểu `int`, dùng để theo dõi số lượng sinh viên thực tế trong mảng.
3.  Thêm **Constructor** cho lớp `LopHoc` nhận vào `tenLop` để khởi tạo.
4.  Viết phương thức `themSinhVien(SinhVien sv)`:
    -   Phương thức nhận vào một **đối tượng** `SinhVien` làm tham số.
    -   Thêm sinh viên này vào mảng `danhSachSV` tại vị trí `soLuongSVHienTai`.
    -   Tăng `soLuongSVHienTai` lên 1.
    -   Kiểm tra nếu lớp đã đầy thì không thêm và thông báo.
5.  Viết phương thức `inDanhSach()`:
    -   Phương thức không có tham số, không trả về giá trị.
    -   In ra tên lớp học.
    -   Dùng vòng lặp `for` để duyệt qua `danhSachSV` (chỉ duyệt đến `soLuongSVHienTai`) và gọi phương thức `hienThiThongTin()` của mỗi đối tượng sinh viên để in thông tin của cả lớp.
6.  **Nâng cao (Tùy chọn):** Nạp chồng phương thức `themSinhVien`.
    -   Viết một phương thức `themSinhVien` khác, nhận vào các tham số: `maSV`, `hoTen`, `diemToan`, `diemLy`, `diemHoa`.
    -   Bên trong phương thức này, hãy tạo một đối tượng `SinhVien` mới từ các tham số nhận vào, sau đó gọi lại phương thức `themSinhVien(SinhVien sv)` đã có để thêm vào danh sách. Đây là ví dụ về **nạp chồng phương thức**.
7.  Cập nhật phương thức `main` trong lớp `QuanLySinhVien`:
    -   Tạo một đối tượng `LopHoc` tên là `lop12A1`.
    -   Tạo các đối tượng `SinhVien` như đã làm ở Bài 2.
    -   Gọi phương thức `themSinhVien()` của đối tượng `lop12A1` để thêm các sinh viên đã tạo vào lớp.
    -   Cuối cùng, gọi phương thức `inDanhSach()` của đối tượng `lop12A1` để xem kết quả danh sách cả lớp.
