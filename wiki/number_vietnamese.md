<!--
Meta Description: # Số (Number) trong JavaScript: Tất cả những gì bạn cần biết ## Tóm tắt Số (Number) trong JavaScript là kiểu dữ liệu cơ bản dùng để biểu diễn các giá ...
Meta Keywords: let, javascript, các, giá, trị
-->

# Số (Number) trong JavaScript: Tất cả những gì bạn cần biết

## Tóm tắt
Số (Number) trong JavaScript là kiểu dữ liệu cơ bản dùng để biểu diễn các giá trị số, bao gồm cả số nguyên và số thập phân. JavaScript sử dụng định dạng IEEE 754 cho các phép toán số học.

## Tài liệu
### Mục đích
Kiểu dữ liệu Number trong JavaScript được sử dụng để thực hiện các phép toán số học, so sánh và nhiều tác vụ khác liên quan đến số. Đây là kiểu dữ liệu duy nhất trong JavaScript để biểu diễn số, không phân biệt giữa số nguyên và số thực.

### Cách sử dụng
Để sử dụng kiểu Number, bạn có thể khai báo biến và gán giá trị số cho nó. Dưới đây là cú pháp cơ bản:

```javascript
let a = 5;          // Số nguyên
let b = 3.14;       // Số thực
let c = -10;        // Số âm
let d = NaN;        // Không phải là số
let e = Infinity;   // Vô cực
```

### Chi tiết
- **Số nguyên**: Là các giá trị số không có phần thập phân (ví dụ: 1, 2, 3).
- **Số thực**: Là các giá trị số có phần thập phân (ví dụ: 1.5, 3.14).
- **NaN**: Là viết tắt của "Not-a-Number", được trả về khi một phép toán không hợp lệ được thực hiện.
- **Infinity**: Biểu diễn giá trị vô cực, được trả về khi một số lớn hơn số tối đa có thể lưu trữ.

## Ví dụ
### Ví dụ cơ bản
```javascript
let x = 10;          // Số nguyên
let y = 2.5;        // Số thực
let sum = x + y;    // Kết quả: 12.5
console.log(sum);   // In ra: 12.5
```

### Ví dụ với NaN và Infinity
```javascript
let a = 0 / 0;      // Kết quả: NaN
let b = 1 / 0;      // Kết quả: Infinity
console.log(a);     // In ra: NaN
console.log(b);     // In ra: Infinity
```

## Giải thích
- **Cách kiểm tra NaN**: Sử dụng hàm `isNaN()`, ví dụ: `isNaN(a)` sẽ trả về `true` nếu `a` là NaN.
- **So sánh số**: Sử dụng các toán tử so sánh (`>`, `<`, `===`, `!==`) để so sánh các giá trị số.
- **Hạn chế về độ chính xác**: Các phép toán số thực có thể dẫn đến lỗi làm tròn. Ví dụ, `0.1 + 0.2` sẽ không trả về `0.3` mà là `0.30000000000000004`.

## Tóm tắt một câu
Kiểu dữ liệu Số (Number) trong JavaScript là cách duy nhất để biểu diễn giá trị số, bao gồm cả số nguyên và số thập phân, với các đặc điểm và hạn chế riêng biệt.