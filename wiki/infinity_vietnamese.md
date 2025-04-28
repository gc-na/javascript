<!--
Meta Description: # Infinity trong JavaScript: Tìm hiểu về Giá trị Vô Cùng ## Tóm tắt Infinity là một giá trị đặc biệt trong JavaScript, đại diện cho số vô cùng. Nó là ...
Meta Keywords: infinity, giá, trị, trong, các
-->

# Infinity trong JavaScript: Tìm hiểu về Giá trị Vô Cùng

## Tóm tắt
Infinity là một giá trị đặc biệt trong JavaScript, đại diện cho số vô cùng. Nó là một phần của kiểu dữ liệu số và được sử dụng trong các phép toán để biểu diễn các giá trị lớn hơn bất kỳ giá trị số nào có thể được đại diện.

## Tài liệu
### Mục đích
Infinity trong JavaScript được sử dụng để biểu thị một giá trị vô hạn, thường xuất hiện trong các phép toán số học khi kết quả vượt quá giới hạn của số thực.

### Cách sử dụng
Infinity có thể được sử dụng trong các phép toán số học, so sánh, và các tình huống khác mà giá trị vô hạn có thể xuất hiện. Đặc biệt, Infinity có thể được truy cập thông qua thuộc tính `Infinity` của đối tượng toàn cục.

### Chi tiết
- **Kiểu dữ liệu**: Infinity là một giá trị kiểu số (number).
- **Giá trị**: Infinity lớn hơn bất kỳ số thực nào. `-Infinity` cũng tồn tại và nó nhỏ hơn bất kỳ số thực nào.
- **Phép toán**: Bất kỳ số dương nào cộng với Infinity sẽ cho ra Infinity. Tương tự, bất kỳ số dương nào nhân với Infinity cũng sẽ cho ra Infinity.

## Ví dụ
### Ví dụ 1: Giá trị Infinity
```javascript
console.log(Infinity); // In ra: Infinity
```

### Ví dụ 2: Phép toán với Infinity
```javascript
console.log(5 + Infinity); // In ra: Infinity
console.log(Infinity * 2); // In ra: Infinity
console.log(-Infinity + 5); // In ra: -Infinity
```

### Ví dụ 3: So sánh với Infinity
```javascript
console.log(1000 < Infinity); // In ra: true
console.log(-Infinity < -1000); // In ra: true
console.log(Infinity === Infinity); // In ra: true
```

## Giải thích
Khi làm việc với Infinity, có một số điều cần lưu ý:
- Infinity không phải là một số thực trong ý nghĩa thông thường, mà là một đại diện cho sự vô hạn.
- Các phép toán với Infinity có thể dẫn đến kết quả không mong muốn nếu không được xử lý đúng cách, chẳng hạn như chia cho 0, sẽ dẫn đến NaN (Not a Number).
- Cần phân biệt giữa Infinity và các giá trị số khác để tránh nhầm lẫn trong các phép toán và điều kiện.

## Tóm tắt một dòng
Infinity trong JavaScript là giá trị đại diện cho số vô hạn, lớn hơn mọi số thực và có thể được sử dụng trong các phép toán số học.