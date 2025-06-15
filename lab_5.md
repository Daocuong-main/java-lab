# Bài Lab 05: Mảng và Lớp ArrayList (Arrays and the ArrayList Class)

- **Môn học:** Lập trình Hướng đối tượng
- **Thời gian:** 120 phút
- **Mục tiêu:**
  - Hiểu và biết cách khai báo, khởi tạo và sử dụng mảng một chiều.
  - Xử lý các phần tử trong mảng: duyệt mảng, tính toán, tìm kiếm.
  - Biết cách truyền mảng như một tham số cho phương thức.
  - Vận dụng một số thuật toán cơ bản trên mảng (tìm giá trị lớn nhất/nhỏ nhất, sắp xếp).
  - Biết cách trả về một mảng từ một phương thức.
  - Làm việc với mảng chuỗi (`String[]`) và mảng đối tượng (`Array of Objects`).
  - Hiểu và sử dụng `ArrayList` như một giải pháp thay thế linh hoạt cho mảng.

---

## Yêu cầu chung

- Tạo một project Java mới trong IDE của bạn.
- Mỗi bài tập nên được thực hiện trong các class riêng biệt để dễ quản lý.
- Đọc kỹ yêu cầu và các gợi ý trước khi bắt đầu code.

---

### **Bài 1: Phân tích Mảng số nguyên (Thời gian dự kiến: 40 phút)**

**Mục tiêu:** Luyện tập các thao tác cơ bản trên mảng kiểu nguyên thủy: nhập, xuất, xử lý và truyền mảng vào phương thức.

**Yêu cầu:**

1.  Tạo một class tên là `ArrayUtils`.
2.  Trong class `ArrayUtils`, viết các **phương thức tĩnh (static)** sau:
    -   `taoMang(int soPhanTu)`:
        -   **Tham số:** Số lượng phần tử của mảng.
        -   **Chức năng:** Yêu cầu người dùng nhập vào giá trị cho từng phần tử của mảng từ bàn phím.
        -   **Trả về:** Mảng `int[]` vừa được tạo và nhập dữ liệu. (Đây là ví dụ về **Returning Arrays from Methods**).
    -   `xuatMang(int[] arr)`:
        -   **Tham số:** Một mảng `int[]`.
        -   **Chức năng:** In tất cả các phần tử của mảng ra màn hình trên một dòng, cách nhau bởi khoảng trắng.
    -   `timMax(int[] arr)`:
        -   **Tham số:** Một mảng `int[]`.
        -   **Chức năng:** Tìm và trả về giá trị lớn nhất trong mảng.
    -   `tinhTong(int[] arr)`:
        -   **Tham số:** Một mảng `int[]`.
        -   **Chức năng:** Tính và trả về tổng các phần tử của mảng.
    -   `demSoLe(int[] arr)`:
        -   **Tham số:** Một mảng `int[]`.
        -   **Chức năng:** Đếm và trả về số lượng các số lẻ trong mảng.

3.  Tạo một class `MainBai1` có phương thức `main` để kiểm tra:
    -   Trong `main`, hỏi người dùng muốn tạo mảng có bao nhiêu phần tử.
    -   Gọi phương thức `taoMang()` để tạo và nhập liệu cho mảng.
    -   Gọi các phương thức `xuatMang()`, `timMax()`, `tinhTong()`, `demSoLe()` để thực thi và in kết quả ra màn hình. (Đây là ví dụ về **Passing Arrays as Arguments**).

**Ví dụ output:**

```
Nhập số lượng phần tử của mảng: 5
Nhập phần tử thứ 0: 12
Nhập phần tử thứ 1: 5
Nhập phần tử thứ 2: -7
Nhập phần tử thứ 3: 9
Nhập phần tử thứ 4: 8
Mảng bạn vừa nhập là: 12 5 -7 9 8 
Giá trị lớn nhất trong mảng là: 12
Tổng các phần tử trong mảng là: 27
Số lượng số lẻ trong mảng là: 3
```

---

### **Bài 2: Quản lý danh sách sinh viên (Thời gian dự kiến: 50 phút)**

**Mục tiêu:** Luyện tập với mảng đối tượng (`Array of Objects`), một khái niệm quan trọng trong lập trình hướng đối tượng.

**Yêu cầu:**

1.  Sử dụng lại lớp `SinhVien` đã tạo ở bài lab trước (hoặc tạo một lớp `SinhVien` mới đơn giản với các thuộc tính: `maSV` (String), `hoTen` (String), `diemTB` (double)). Thêm một phương thức `hienThi()` để in thông tin sinh viên.

2.  Tạo một class `DanhSachSinhVien` để quản lý một danh sách sinh viên. Class này có các thành phần sau:
    -   Một thuộc tính là mảng đối tượng `SinhVien[]`: `private SinhVien[] ds;`
    -   Một thuộc tính `count` để đếm số sinh viên hiện có.
    -   **Constructor:** Nhận vào kích thước tối đa của danh sách và khởi tạo mảng `ds`.
    -   **Phương thức `themSinhVien(SinhVien sv)`:** Thêm một sinh viên vào danh sách.
    -   **Phương thức `xuatDanhSach()`:** In thông tin của tất cả sinh viên trong danh sách.
    -   **Phương thức `sapXepTheoDiem()`:** Sắp xếp danh sách sinh viên giảm dần theo điểm trung bình. (Gợi ý: Sử dụng thuật toán sắp xếp nổi bọt - Bubble Sort hoặc lựa chọn - Selection Sort).
    -   **Phương thức `timKiemTheoTen(String ten)`:** Tìm kiếm và hiển thị thông tin của các sinh viên có tên chứa chuỗi `ten` được nhập vào.

3.  Tạo class `MainBai2` với phương thức `main` để:
    -   Tạo một đối tượng `DanhSachSinhVien` với kích thước là 5.
    -   Tạo 3-4 đối tượng `SinhVien` với dữ liệu cứng (hard-code).
    -   Thêm các sinh viên này vào danh sách.
    -   Gọi phương thức `xuatDanhSach()` để hiển thị danh sách ban đầu.
    -   Gọi phương thức `sapXepTheoDiem()` rồi gọi lại `xuatDanhSach()` để xem kết quả sau khi sắp xếp.
    -   Yêu cầu người dùng nhập một tên và gọi phương thức `timKiemTheoTen()` để kiểm tra.

---

### **Bài 3: Sử dụng `ArrayList` (Thời gian dự kiến: 30 phút)**

**Mục tiêu:** Hiểu được sự tiện lợi và linh hoạt của `ArrayList` so với mảng thông thường.

**Yêu cầu:**

Thực hiện lại **Bài 2** nhưng thay thế mảng `SinhVien[]` bằng `ArrayList<SinhVien>`.

1.  Tạo một class mới tên là `DanhSachSinhVien_ArrayList`.
2.  Thay đổi thuộc tính `private SinhVien[] ds;` thành `private ArrayList<SinhVien> ds;`.
3.  Chỉnh sửa lại các phương thức cho phù hợp với `ArrayList`:
    -   **Constructor:** Không cần nhận kích thước, chỉ cần khởi tạo `ds = new ArrayList<>();`.
    -   **Phương thức `themSinhVien(SinhVien sv)`:** Sử dụng phương thức `ds.add(sv)`.
    -   **Phương thức `xuatDanhSach()`:** Dùng vòng lặp `for-each` hoặc `ds.size()` để duyệt.
    -   **Phương thức `sapXepTheoDiem()`:** Sử dụng `Collections.sort()` với một `Comparator` tùy chỉnh để sắp xếp. Đây là cách làm hiệu quả và chuyên nghiệp hơn.
        ```java
        // Gợi ý
        ds.sort((sv1, sv2) -> Double.compare(sv2.getDiemTB(), sv1.getDiemTB()));
        ```
    -   **Phương thức `timKiemTheoTen(String ten)`:** Vẫn duyệt qua danh sách và kiểm tra như cũ.

4.  Tạo class `MainBai3` để kiểm tra các chức năng của `DanhSachSinhVien_ArrayList`. Bạn sẽ thấy việc thêm, xóa (nếu có) và quản lý danh sách trở nên đơn giản hơn nhiều.
