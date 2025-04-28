<!--
Meta Description: # Escape trong JavaScript: Cách Sử Dụng và Ý Nghĩa ## Tóm tắt Trong JavaScript, hàm `escape` được sử dụng để mã hóa một chuỗi bằng cách chuyển đổi các...
Meta Keywords: các, hàm, escape, trong, dụng
-->

# Escape trong JavaScript: Cách Sử Dụng và Ý Nghĩa

## Tóm tắt
Trong JavaScript, hàm `escape` được sử dụng để mã hóa một chuỗi bằng cách chuyển đổi các ký tự đặc biệt thành các ký tự tương ứng trong mã ASCII. Tuy nhiên, hàm này đã được đánh dấu là lỗi thời và không nên được sử dụng trong mã mới.

## Tài liệu
### Mục đích
Hàm `escape` trong JavaScript được thiết kế để mã hóa các ký tự không an toàn trong chuỗi, giúp đảm bảo rằng chuỗi đó có thể được sử dụng trong các ngữ cảnh khác nhau mà không gây ra lỗi.

### Cú pháp
```javascript
escape(str)
```
- **str**: Chuỗi cần mã hóa.

### Chi tiết
Hàm `escape` chuyển đổi các ký tự không phải ASCII thành mã hex tương ứng. Ví dụ, ký tự khoảng trắng sẽ được chuyển đổi thành `%20`. Tuy nhiên, hàm này không xử lý một số ký tự Unicode và có thể để lại một số ký tự không được mã hóa đúng cách.

### Lưu ý
- Hàm `escape` đã bị đánh dấu là lỗi thời và không nên sử dụng trong mã mới. Thay vào đó, bạn nên sử dụng các hàm như `encodeURIComponent` hoặc `encodeURI` để mã hóa URL.
- Việc sử dụng hàm `escape` có thể dẫn đến các vấn đề bảo mật nếu không được sử dụng cẩn thận.

## Ví dụ
### Ví dụ cơ bản
```javascript
let originalString = "Hello World!";
let escapedString = escape(originalString);
console.log(escapedString); // Kết quả: "Hello%20World%21"
```

### Ví dụ với ký tự đặc biệt
```javascript
let specialChars = "JavaScript & HTML < > ' \"";
let escapedSpecialChars = escape(specialChars);
console.log(escapedSpecialChars); // Kết quả: "JavaScript%20%26%20HTML%20%3C%20%3E%20%27%20%22"
```

## Giải thích
Hàm `escape` không mã hóa tất cả các ký tự đặc biệt và có thể để lại các ký tự Unicode không được mã hóa. Điều này có thể dẫn đến các lỗi trong việc xử lý chuỗi hoặc bảo mật khi sử dụng trong các ứng dụng web. Do đó, việc sử dụng các hàm mã hóa hiện đại như `encodeURIComponent` là rất quan trọng để đảm bảo rằng chuỗi được mã hóa đúng cách.

## Tóm tắt một dòng
Hàm `escape` trong JavaScript dùng để mã hóa chuỗi nhưng đã lỗi thời và nên được thay thế bằng các hàm mã hóa hiện đại như `encodeURIComponent`.