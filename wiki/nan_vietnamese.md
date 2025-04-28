<!--
Meta Description: # NaN trong JavaScript: Hiểu và Sử Dụng ## Tóm tắt NaN (Not-a-Number) là một giá trị đặc biệt trong JavaScript, được sử dụng để chỉ ra rằng một giá tr...
Meta Keywords: nan, isnan, giá, trị, không
-->

# NaN trong JavaScript: Hiểu và Sử Dụng

## Tóm tắt
NaN (Not-a-Number) là một giá trị đặc biệt trong JavaScript, được sử dụng để chỉ ra rằng một giá trị không phải là một số hợp lệ. NaN thường xuất hiện khi thực hiện các phép toán không hợp lệ hoặc khi chuyển đổi một giá trị không phải số sang số.

## Tài liệu
### Mục đích
NaN được sử dụng để xử lý các tình huống mà kết quả của một phép toán không thể xác định được. Điều này giúp lập trình viên nhận biết và xử lý các giá trị không hợp lệ trong các phép tính số học.

### Cách sử dụng
Trong JavaScript, NaN có thể được tạo ra từ nhiều nguồn khác nhau, bao gồm:
- Phép chia 0/0
- Kết quả của các phép toán không hợp lệ, chẳng hạn như "abc" - 1
- Chuyển đổi một giá trị không phải số sang số, ví dụ: Number("abc")

Để kiểm tra xem một giá trị có phải là NaN hay không, bạn có thể sử dụng hàm `isNaN()` hoặc `Number.isNaN()`. Tuy nhiên, `isNaN()` có thể trả về true cho các giá trị không phải số khác, trong khi `Number.isNaN()` chỉ trả về true cho giá trị NaN.

### Ví dụ
```javascript
console.log(NaN); // In ra: NaN

console.log(0 / 0); // In ra: NaN

console.log("abc" - 1); // In ra: NaN

console.log(isNaN(NaN)); // In ra: true
console.log(isNaN("abc")); // In ra: true (có thể gây nhầm lẫn)

console.log(Number.isNaN(NaN)); // In ra: true
console.log(Number.isNaN("abc")); // In ra: false
```

## Giải thích
### Những cạm bẫy thường gặp
1. **Kiểm tra NaN**: Sử dụng `===` để so sánh NaN với chính nó sẽ luôn trả về false. Do đó, bạn nên sử dụng `isNaN()` hoặc `Number.isNaN()` để kiểm tra NaN.

2. **Sự khác biệt giữa isNaN và Number.isNaN**: `isNaN()` sẽ cố gắng chuyển đổi giá trị truyền vào thành số trước khi kiểm tra, trong khi `Number.isNaN()` chỉ kiểm tra giá trị để xem nó có phải là NaN hay không.

3. **Sử dụng NaN trong tính toán**: Bất kỳ phép toán nào kết hợp với NaN sẽ đều cho kết quả là NaN. Điều này có thể gây ra vấn đề nếu không được xử lý đúng cách.

### Ghi chú bổ sung
NaN là một trong những giá trị đặc biệt trong JavaScript và không thể so sánh trực tiếp với các giá trị khác. Để rõ ràng hơn, bạn nên thường xuyên sử dụng các hàm kiểm tra để tránh lỗi trong mã.

## Tóm tắt một câu
NaN trong JavaScript là một giá trị đặc biệt được sử dụng để chỉ ra rằng kết quả của một phép toán không phải là một số hợp lệ.