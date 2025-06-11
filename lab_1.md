# LAB: JAVA FUNDAMENTALS VÀ DECISION STRUCTURES

**Thời gian:** 2 tiếng  
**Điểm:** 100 điểm  
**Ngôn ngữ:** Java

## YÊU CẦU CHUNG
- Đặt tên class theo quy ước PascalCase
- Đặt tên biến theo quy ước camelCase
- Thêm comment giải thích logic chính
- Test các trường hợp edge case

---

## BÀI 1: TÍNH TOÁN CƠ BẢN (20 điểm)

Viết chương trình `BasicCalculator.java` thực hiện:

1. Nhập 2 số thực từ bàn phím
2. Tính và hiển thị:
   - Tổng, hiệu, tích, thương
   - Số lớn hơn và nhỏ hơn
   - Trung bình cộng
   - Phần nguyên và phần dư khi chia số nguyên đầu tiên cho số nguyên thứ hai

**Input mẫu:**
```
Nhập số thứ nhất: 15.5
Nhập số thứ hai: 4.2
```

**Output mẫu:**
```
Tổng: 19.7
Hiệu: 11.3
Tích: 65.1
Thương: 3.69
Số lớn hơn: 15.5
Số nhỏ hơn: 4.2
Trung bình: 9.85
Phần nguyên: 3
Phần dư: 3
```

---

## BÀI 2: PHÂN LOẠI TAM GIÁC (25 điểm)

Viết chương trình `TriangleClassifier.java`:

1. Nhập độ dài 3 cạnh của tam giác
2. Kiểm tra tính hợp lệ của tam giác
3. Phân loại tam giác theo cạnh và góc:
   - Theo cạnh: đều, cân, thường
   - Theo góc: vuông, nhọn, tù

**Điều kiện:**
- Tam giác hợp lệ: tổng 2 cạnh > cạnh còn lại
- Tam giác vuông: a² + b² = c² (với c là cạnh lớn nhất)
- Tam giác tù: a² + b² < c²
- Tam giác nhọn: a² + b² > c²

**Input mẫu:**
```
Nhập cạnh a: 3
Nhập cạnh b: 4
Nhập cạnh c: 5
```

**Output mẫu:**
```
Tam giác hợp lệ
Tam giác thường
Tam giác vuông
```

---

## BÀI 3: HỆ THỐNG TÍNH LƯƠNG (30 điểm)

Viết chương trình `SalaryCalculator.java` tính lương nhân viên:

**Quy định:**
- Lương cơ bản: 5,000,000 VND
- Hệ số lương theo cấp bậc:
  - Intern (I): 1.0
  - Fresher (F): 1.2
  - Junior (J): 1.5
  - Senior (S): 2.0
  - Lead (L): 2.5
- Phụ cấp theo kinh nghiệm:
  - < 1 năm: 0 VND
  - 1-3 năm: 500,000 VND
  - 3-5 năm: 1,000,000 VND
  - > 5 năm: 1,500,000 VND
- Thuế TNCN:
  - <= 10 triệu: 0%
  - 10-15 triệu: 5%
  - 15-20 triệu: 10%
  - > 20 triệu: 15%

**Input:**
```
Nhập cấp bậc (I/F/J/S/L): S
Nhập số năm kinh nghiệm: 3.5
```

**Output:**
```
Lương cơ bản: 5,000,000 VND
Hệ số lương: 2.0
Lương theo hệ số: 10,000,000 VND
Phụ cấp kinh nghiệm: 1,000,000 VND
Tổng lương trước thuế: 11,000,000 VND
Thuế TNCN (5%): 550,000 VND
Lương thực nhận: 10,450,000 VND
```

---

## BÀI 4: GAME ĐOÁN SỐ (25 điểm)

Viết chương trình `NumberGuessingGame.java`:

**Quy tắc:**
1. Chương trình random số từ 1-100
2. Người chơi có tối đa 7 lần đoán
3. Mỗi lần đoán sai, hiển thị gợi ý "cao hơn" hoặc "thấp hơn"
4. Tính điểm dựa trên số lần đoán:
   - 1 lần: 100 điểm
   - 2 lần: 90 điểm
   - 3 lần: 80 điểm
   - 4 lần: 70 điểm
   - 5 lần: 60 điểm
   - 6 lần: 50 điểm
   - 7 lần: 40 điểm
   - Không đoán được: 0 điểm

**Gameplay mẫu:**
```
=== GAME ĐOÁN SỐ ===
Tôi đã nghĩ ra một số từ 1 đến 100. Bạn có 7 lần đoán!

Lần đoán 1/7: 50
Số cần tìm lớn hơn 50

Lần đoán 2/7: 75
Số cần tìm nhỏ hơn 75

Lần đoán 3/7: 63
Chúc mừng! Bạn đã đoán đúng!
Điểm số: 80 điểm
```

---

## LƯU Ý QUAN TRỌNG

1. **Validation dữ liệu:** Kiểm tra input không hợp lệ
2. **Edge cases:** Test với các giá trị biên
3. **Code style:** Tuân thủ Java naming convention
4. **Performance:** Tối ưu logic, tránh redundant code
5. **User experience:** Interface rõ ràng, dễ sử dụng

**Thời gian nộp bài:** Cuối buổi lab  
**Format nộp:** File .java hoặc project folder đã zip
