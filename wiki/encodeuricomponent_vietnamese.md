<!--
Meta Description: # encodeURIComponent trong JavaScript: Hướng Dẫn Chi Tiết ## Tóm tắt `encodeURIComponent` là một hàm trong JavaScript dùng để mã hóa các thành phần củ...
Meta Keywords: hóa, encodeuricomponent, các, url, javascript
-->

# encodeURIComponent trong JavaScript: Hướng Dẫn Chi Tiết

## Tóm tắt
`encodeURIComponent` là một hàm trong JavaScript dùng để mã hóa các thành phần của URI (Uniform Resource Identifier) bằng cách thay thế các ký tự đặc biệt bằng mã hex tương ứng. Hàm này rất hữu ích trong việc bảo đảm rằng các thông tin truyền qua URL không bị biến đổi hoặc hiểu sai.

## Tài liệu

### Mục đích
Hàm `encodeURIComponent` được sử dụng để mã hóa các thành phần của URI, như tham số truy vấn trong URL. Điều này giúp các ký tự đặc biệt như dấu cách, dấu hỏi, và các ký tự không an toàn khác được biểu diễn một cách an toàn trong URL.

### Cú pháp
```javascript
encodeURIComponent(uriComponent);
```

### Tham số
- `uriComponent`: Một chuỗi (string) cần được mã hóa.

### Giá trị trả về
Hàm trả về một chuỗi đã được mã hóa, trong đó các ký tự đặc biệt được thay thế bằng mã hex.

### Lưu ý
- Không mã hóa các ký tự: `! * ' ( )` và một số ký tự khác không được mã hóa.
- Nếu bạn cần mã hóa toàn bộ URL, hãy sử dụng `encodeURI` thay vì `encodeURIComponent`.

## Ví dụ

### Ví dụ 1: Mã hóa một chuỗi đơn giản
```javascript
let str = "Hello World!";
let encodedStr = encodeURIComponent(str);
console.log(encodedStr); // "Hello%20World%21"
```

### Ví dụ 2: Mã hóa tham số URL
```javascript
let param = "name=John Doe & age=30";
let encodedParam = encodeURIComponent(param);
console.log(encodedParam); // "name%3DJohn%20Doe%20%26%20age%3D30"
```

### Ví dụ 3: Sử dụng trong URL
```javascript
let baseUrl = "https://example.com/search";
let query = "JavaScript & HTML";
let fullUrl = `${baseUrl}?query=${encodeURIComponent(query)}`;
console.log(fullUrl); // "https://example.com/search?query=JavaScript%20%26%20HTML"
```

## Giải thích
Một số vấn đề thường gặp khi sử dụng `encodeURIComponent` bao gồm:
- **Không mã hóa toàn bộ URL**: Nếu bạn cố gắng mã hóa toàn bộ URL bằng `encodeURIComponent`, bạn có thể gặp lỗi. Chỉ mã hóa các thành phần cụ thể của URL như tham số truy vấn.
- **Ký tự không cần mã hóa**: Một số ký tự như `~`, `!`, `*`, `'`, `(` và `)` không cần phải mã hóa và sẽ được giữ nguyên khi sử dụng hàm này.

## Tóm tắt một câu
`encodeURIComponent` là hàm JavaScript dùng để mã hóa các thành phần của URI, giúp đảm bảo rằng thông tin truyền qua URL được bảo vệ an toàn.