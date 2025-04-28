<!--
Meta Description: # Văn bản trong JavaScript: Cách Sử Dụng và Tính Năng ## Tóm tắt Trong JavaScript, "văn bản" chủ yếu đề cập đến kiểu dữ liệu chuỗi, cho phép người dùn...
Meta Keywords: chuỗi, javascript, với, bản, văn
-->

# Văn bản trong JavaScript: Cách Sử Dụng và Tính Năng

## Tóm tắt
Trong JavaScript, "văn bản" chủ yếu đề cập đến kiểu dữ liệu chuỗi, cho phép người dùng lưu trữ và thao tác với dữ liệu dạng văn bản. Các thao tác với chuỗi bao gồm tạo, truy xuất, và chỉnh sửa dữ liệu văn bản.

## Tài liệu
### Mục đích
Chuỗi là một kiểu dữ liệu cơ bản trong JavaScript, dùng để đại diện cho văn bản. Chúng có thể chứa ký tự, số, và các ký tự đặc biệt. Các chuỗi trong JavaScript được bao quanh bởi dấu nháy đơn (`'`), dấu nháy kép (`"`), hoặc dấu nháy ngược (`\``) cho template literals.

### Cách sử dụng
Để tạo một chuỗi trong JavaScript, bạn có thể sử dụng cú pháp sau:
```javascript
let str1 = 'Hello, World!';
let str2 = "Chào mừng đến với JavaScript!";
let str3 = `Dòng văn bản từ biến: ${str1}`;
```

### Chi tiết
- **Kết nối chuỗi**: Bạn có thể kết nối các chuỗi với nhau bằng toán tử `+`.
  ```javascript
  let greeting = str1 + ' ' + str2; // "Hello, World! Chào mừng đến với JavaScript!"
  ```

- **Các phương thức chuỗi**: JavaScript cung cấp nhiều phương thức để thao tác với chuỗi như:
  - `length`: lấy độ dài của chuỗi.
  - `toUpperCase()`: chuyển đổi chuỗi thành chữ hoa.
  - `toLowerCase()`: chuyển đổi chuỗi thành chữ thường.
  - `charAt(index)`: lấy ký tự tại vị trí chỉ định.
  - `substring(start, end)`: lấy phần của chuỗi trong khoảng từ start đến end.

### Ví dụ
```javascript
let text = "Học JavaScript";
console.log(text.length); // 15
console.log(text.toUpperCase()); // HỌC JAVASCRIPT
console.log(text.charAt(0)); // H
console.log(text.substring(0, 4)); // Học
```

## Giải thích
Một số lỗi thường gặp khi làm việc với chuỗi bao gồm:
- **Quên dấu nháy**: Nếu không bao quanh chuỗi bằng dấu nháy, bạn sẽ gặp lỗi cú pháp.
- **Sử dụng không đúng phương thức**: Một số phương thức không thay đổi chuỗi gốc mà trả về một chuỗi mới.
- **Kết nối chuỗi với đối tượng không phải là chuỗi**: Điều này có thể dẫn đến kết quả không mong muốn.

## Tóm tắt một dòng
Chuỗi trong JavaScript cho phép lưu trữ và thao tác với dữ liệu văn bản một cách linh hoạt và hiệu quả.