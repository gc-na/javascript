<!--
Meta Description: # decodeURI: Giải mã URI trong JavaScript ## Tóm tắt `decodeURI` là một hàm trong JavaScript được sử dụng để giải mã một chuỗi URI đã được mã hóa, giú...
Meta Keywords: giải, một, decodeuri, uri, được
-->

# decodeURI: Giải mã URI trong JavaScript

## Tóm tắt
`decodeURI` là một hàm trong JavaScript được sử dụng để giải mã một chuỗi URI đã được mã hóa, giúp chuyển đổi các ký tự mã hóa trở lại thành dạng gốc.

## Tài liệu
Hàm `decodeURI` trong JavaScript có mục đích chính là giải mã một chuỗi URI đã được mã hóa bằng hàm `encodeURI`. URI (Uniform Resource Identifier) có thể chứa các ký tự đặc biệt mà cần phải được mã hóa để sử dụng trong URL. Hàm này sẽ chuyển đổi các ký tự mã hóa, chẳng hạn như `%20` thành dấu cách (` `).

### Cú pháp
```javascript
decodeURI(encodedURI)
```

### Tham số
- `encodedURI`: Chuỗi URI đã được mã hóa mà bạn muốn giải mã. 

### Giá trị trả về
Hàm trả về một chuỗi đã được giải mã, với tất cả các ký tự mã hóa được chuyển đổi thành ký tự tương ứng của chúng.

## Ví dụ
Dưới đây là một số ví dụ về cách sử dụng hàm `decodeURI`:

### Ví dụ 1: Giải mã một URI đơn giản
```javascript
const encodedURI = "https%3A%2F%2Fwww.example.com%2F";
const decodedURI = decodeURI(encodedURI);
console.log(decodedURI); // Kết quả: https://www.example.com/
```

### Ví dụ 2: Giải mã nhiều ký tự đặc biệt
```javascript
const encodedURI = "Hello%20World%21%20JavaScript%20is%20fun%21";
const decodedURI = decodeURI(encodedURI);
console.log(decodedURI); // Kết quả: Hello World! JavaScript is fun!
```

## Giải thích
Khi sử dụng `decodeURI`, cần lưu ý một số điểm sau:
- `decodeURI` không giải mã các ký tự được sử dụng trong các thành phần của URI như `#`, `?`, và `&`. Nếu bạn cần giải mã một URI đầy đủ bao gồm các ký tự này, hãy sử dụng `decodeURIComponent`.
- Nếu chuỗi đầu vào không phải là một URI hợp lệ, hàm có thể ném ra một lỗi `URIError`. Do đó, việc kiểm tra tính hợp lệ của chuỗi trước khi giải mã là rất quan trọng để tránh lỗi.

## Tóm tắt một dòng
Hàm `decodeURI` trong JavaScript được sử dụng để giải mã các chuỗi URI đã được mã hóa, chuyển đổi ký tự mã hóa trở lại dạng gốc.