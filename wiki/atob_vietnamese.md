<!--
Meta Description: # atob trong JavaScript: Giải mã Chuỗi Base64 ## Tóm Tắt `atob` là một hàm trong JavaScript được sử dụng để giải mã các chuỗi đã được mã hóa ở định dạ...
Meta Keywords: chuỗi, hóa, base64, giải, atob
-->

# atob trong JavaScript: Giải mã Chuỗi Base64

## Tóm Tắt
`atob` là một hàm trong JavaScript được sử dụng để giải mã các chuỗi đã được mã hóa ở định dạng Base64. Hàm này rất hữu ích trong việc xử lý dữ liệu nhị phân và các chuỗi thông tin được truyền qua mạng.

## Tài Liệu
Hàm `atob` (ASCII to Binary) chuyển đổi một chuỗi mã hóa Base64 thành chuỗi ký tự ASCII. Hàm này thường được sử dụng khi bạn cần giải mã dữ liệu đã được mã hóa trước đó để xử lý hoặc hiển thị.

### Cú pháp
```javascript
let decodedString = atob(encodedString);
```

### Tham số
- `encodedString`: Một chuỗi được mã hóa ở định dạng Base64 mà bạn muốn giải mã.

### Trả về
Hàm `atob` trả về một chuỗi đã được giải mã từ chuỗi mã hóa Base64.

## Ví dụ
### Ví dụ 1: Giải mã một chuỗi đơn giản
```javascript
let encoded = "SGVsbG8gd29ybGQ="; // "Hello world" được mã hóa Base64
let decoded = atob(encoded);
console.log(decoded); // Kết quả: "Hello world"
```

### Ví dụ 2: Giải mã chuỗi với ký tự đặc biệt
```javascript
let encodedSpecial = "JUMwJDEwJDEw"; // "10$10" được mã hóa Base64
let decodedSpecial = atob(encodedSpecial);
console.log(decodedSpecial); // Kết quả: "10$10"
```

## Giải Thích
Mặc dù `atob` rất hữu ích, có một số điểm cần lưu ý khi sử dụng:
- **Ký tự không hợp lệ**: Nếu chuỗi đầu vào không phải là chuỗi mã hóa Base64 hợp lệ, hàm sẽ ném ra ngoại lệ `InvalidCharacterError`.
- **Hỗ trợ mã hóa**: Chỉ hỗ trợ mã hóa Base64 tiêu chuẩn. Nếu bạn sử dụng các biến thể khác của Base64 (như Base64 URL), bạn sẽ cần điều chỉnh chuỗi đầu vào trước khi giải mã.
- **Mã hóa UTF-8**: `atob` không hỗ trợ mã hóa ký tự UTF-8. Để giải mã dữ liệu UTF-8, bạn cần sử dụng các phương thức bổ sung (như `decodeURIComponent` kết hợp với `escape`).

## Tóm Tắt Một Dòng
Hàm `atob` trong JavaScript là công cụ giải mã hiệu quả cho các chuỗi được mã hóa Base64, giúp chuyển đổi dữ liệu về định dạng ASCII dễ sử dụng.