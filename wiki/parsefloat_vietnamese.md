<!--
Meta Description: # Hàm parseFloat trong JavaScript: Hướng dẫn chi tiết và ứng dụng ## Tóm tắt Hàm `parseFloat` trong JavaScript được sử dụng để phân tích một chuỗi và ...
Meta Keywords: parsefloat, chuỗi, không, quả, hàm
-->

# Hàm parseFloat trong JavaScript: Hướng dẫn chi tiết và ứng dụng

## Tóm tắt
Hàm `parseFloat` trong JavaScript được sử dụng để phân tích một chuỗi và chuyển đổi nó thành số thực (số thập phân). Đây là một công cụ hữu ích trong việc xử lý các phép toán và dữ liệu số.

## Tài liệu
### Mục đích
Hàm `parseFloat` giúp chuyển đổi một chuỗi chứa số thành kiểu dữ liệu số thực. Điều này rất cần thiết khi bạn làm việc với các giá trị số trong chuỗi, chẳng hạn như khi nhận dữ liệu từ người dùng hoặc từ API.

### Cú pháp
```javascript
parseFloat(string)
```

- **string**: Chuỗi cần phân tích. Nếu chuỗi bắt đầu bằng một số, hàm sẽ trả về giá trị số thực đầu tiên được tìm thấy. Nếu chuỗi không bắt đầu bằng số, hàm sẽ trả về `NaN` (Not-a-Number).

### Chi tiết
- Hàm `parseFloat` sẽ đọc chuỗi từ trái sang phải cho đến khi gặp ký tự không phải số.
- Nó hỗ trợ các ký tự thập phân và ký tự `-` (dấu trừ) để biểu thị số âm.
- Nếu chuỗi là rỗng hoặc không chứa số, kết quả sẽ là `NaN`.
- Hàm không làm tròn số và sẽ giữ nguyên phần thập phân.

## Ví dụ
### Ví dụ cơ bản
```javascript
console.log(parseFloat("3.14")); // Kết quả: 3.14
console.log(parseFloat("10.5abc")); // Kết quả: 10.5
console.log(parseFloat("abc10.5")); // Kết quả: NaN
console.log(parseFloat("  -42.5 ")); // Kết quả: -42.5
```

### Ví dụ với các trường hợp đặc biệt
```javascript
console.log(parseFloat("0.1")); // Kết quả: 0.1
console.log(parseFloat("123")); // Kết quả: 123
console.log(parseFloat("")); // Kết quả: NaN
console.log(parseFloat("   -1.5e3")); // Kết quả: -1500
```

## Giải thích
### Những cạm bẫy phổ biến
- **NaN (Not-a-Number)**: Nếu chuỗi không bắt đầu bằng số, hàm sẽ trả về `NaN`. Điều này có thể gây khó khăn trong các phép toán sau này nếu không được xử lý.
  
- **Không làm tròn số**: `parseFloat` không làm tròn số. Nếu bạn cần làm tròn, bạn sẽ phải sử dụng các phương pháp khác như `Math.round`.

- **Không nhận diện dấu phân cách**: `parseFloat` không hỗ trợ dấu phân cách hàng nghìn (ví dụ: "1,000"). Chuỗi này sẽ trả về `1` vì nó sẽ ngừng phân tích tại dấu phẩy.

## Tóm tắt một dòng
Hàm `parseFloat` trong JavaScript chuyển đổi chuỗi thành số thực, giúp xử lý các giá trị số trong lập trình một cách hiệu quả.