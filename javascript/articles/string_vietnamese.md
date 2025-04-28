<!--
Meta Description: # Chuỗi trong JavaScript: Tính năng, Cách sử dụng và Ví dụ ## Tóm tắt Chuỗi trong JavaScript là kiểu dữ liệu cơ bản dùng để đại diện cho văn bản. Nó c...
Meta Keywords: chuỗi, javascript, trong, dụng, let
-->

# Chuỗi trong JavaScript: Tính năng, Cách sử dụng và Ví dụ

## Tóm tắt
Chuỗi trong JavaScript là kiểu dữ liệu cơ bản dùng để đại diện cho văn bản. Nó cho phép lập trình viên xử lý và thao tác với các đoạn văn bản một cách hiệu quả.

## Tài liệu
### Mục đích
Chuỗi trong JavaScript được sử dụng để lưu trữ và thao tác với dữ liệu văn bản. Nó có thể được định nghĩa bằng cách sử dụng dấu nháy đơn (`'`), dấu nháy kép (`"`), hoặc dấu nháy ngược (`` ` ``) cho chuỗi đa dòng.

### Cách sử dụng
Chuỗi có thể được khởi tạo bằng cách sử dụng cú pháp sau:
```javascript
let string1 = 'Xin chào';
let string2 = "Thế giới";
let string3 = `Chào mừng đến với ${string2}`;
```

### Chi tiết
- **Độ dài chuỗi**: Sử dụng thuộc tính `.length` để lấy độ dài của chuỗi.
- **Truy cập ký tự**: Sử dụng chỉ số để truy cập ký tự trong chuỗi, bắt đầu từ 0.
- **Các phương thức chuỗi**: JavaScript cung cấp nhiều phương thức hữu ích như `.toUpperCase()`, `.toLowerCase()`, `.trim()`, `.substring()`, và nhiều phương thức khác để thao tác với chuỗi.

## Ví dụ
### Khởi tạo chuỗi
```javascript
let greeting = "Xin chào!";
console.log(greeting); // In ra: Xin chào!
```

### Độ dài chuỗi
```javascript
let message = "Học JavaScript";
console.log(message.length); // In ra: 15
```

### Truy cập ký tự trong chuỗi
```javascript
let word = "JavaScript";
console.log(word[0]); // In ra: J
```

### Phương thức chuỗi
```javascript
let text = "     Học lập trình JavaScript     ";
console.log(text.trim()); // In ra: "Học lập trình JavaScript"
```

## Giải thích
Một số điểm cần lưu ý khi làm việc với chuỗi trong JavaScript:
- **Không thay đổi**: Chuỗi là kiểu dữ liệu không thay đổi (immutable). Điều này có nghĩa là bạn không thể thay đổi một chuỗi đã được khởi tạo. Mọi thao tác biến đổi sẽ tạo ra một chuỗi mới.
- **Phân biệt chữ hoa chữ thường**: JavaScript phân biệt chữ hoa và chữ thường trong chuỗi. Ví dụ, "abc" và "ABC" được coi là khác nhau.
- **Ký tự đặc biệt**: Để sử dụng các ký tự đặc biệt như dấu nháy trong chuỗi, bạn cần sử dụng ký tự thoát (`\`).

## Tóm tắt một dòng
Chuỗi trong JavaScript là kiểu dữ liệu dùng để đại diện cho văn bản, cho phép lập trình viên thao tác và xử lý văn bản một cách hiệu quả.