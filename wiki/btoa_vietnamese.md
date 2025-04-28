<!--
Meta Description: # Btoa trong JavaScript: Chuyển đổi Chuỗi sang Base64 ## Tóm tắt Btoa là một hàm trong JavaScript được sử dụng để chuyển đổi chuỗi sang định dạng Base...
Meta Keywords: chuỗi, btoa, hàm, hóa, trong
-->

# Btoa trong JavaScript: Chuyển đổi Chuỗi sang Base64

## Tóm tắt
Btoa là một hàm trong JavaScript được sử dụng để chuyển đổi chuỗi sang định dạng Base64. Hàm này hữu ích trong việc mã hóa dữ liệu để truyền tải qua Internet.

## Tài liệu
Btoa (viết tắt của "binary to ASCII") là một hàm toàn cục trong JavaScript, có sẵn trong môi trường trình duyệt. Nó cho phép bạn mã hóa một chuỗi ký tự thành định dạng Base64, giúp dễ dàng truyền tải dữ liệu trong các yêu cầu HTTP hoặc lưu trữ dữ liệu nhị phân.

### Cú pháp
```javascript
btoa(string);
```

### Tham số
- **string**: Một chuỗi ký tự ASCII cần được mã hóa thành Base64. Chuỗi này phải được mã hóa ở định dạng UTF-8, nếu không, hàm sẽ ném ra lỗi `InvalidCharacterError`.

### Giá trị trả về
Hàm `btoa` trả về một chuỗi đã được mã hóa ở định dạng Base64.

## Ví dụ
Dưới đây là một số ví dụ về cách sử dụng hàm `btoa`:

### Ví dụ 1: Mã hóa một chuỗi đơn giản
```javascript
let originalString = "Hello, World!";
let encodedString = btoa(originalString);
console.log(encodedString); // "SGVsbG8sIFdvcmxkIQ=="
```

### Ví dụ 2: Mã hóa chuỗi có ký tự đặc biệt
```javascript
let specialString = "Chào bạn!";
let encodedSpecialString = btoa(specialString);
console.log(encodedSpecialString); // Lỗi: InvalidCharacterError
```

### Ví dụ 3: Mã hóa chuỗi UTF-8
```javascript
let utf8String = unescape(encodeURIComponent("Chào bạn!"));
let encodedUtf8String = btoa(utf8String);
console.log(encodedUtf8String); // "w6AgYmFuxI=="
```

## Giải thích
Khi sử dụng hàm `btoa`, cần lưu ý một số điểm sau:
- **Ký tự ASCII**: Hàm chỉ chấp nhận chuỗi ASCII. Nếu chuỗi chứa ký tự không phải ASCII (như tiếng Việt), bạn cần mã hóa nó thành UTF-8 trước khi sử dụng `btoa`.
- **Lỗi InvalidCharacterError**: Nếu bạn cố gắng mã hóa một chuỗi có ký tự không hợp lệ, hàm sẽ ném ra lỗi này.

Ngoài ra, hàm này không hoạt động trong môi trường Node.js mà chỉ có sẵn trong trình duyệt.

## Tóm tắt ngắn gọn
Hàm `btoa` trong JavaScript cho phép mã hóa chuỗi ASCII thành định dạng Base64, hỗ trợ truyền tải dữ liệu qua Internet.