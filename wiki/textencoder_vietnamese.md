<!--
Meta Description: # TextEncoder trong JavaScript: Mã hóa chuỗi thành định dạng nhị phân ## Tóm tắt `TextEncoder` là một API trong JavaScript cho phép lập trình viên mã ...
Meta Keywords: hóa, textencoder, chuỗi, một, các
-->

# TextEncoder trong JavaScript: Mã hóa chuỗi thành định dạng nhị phân

## Tóm tắt
`TextEncoder` là một API trong JavaScript cho phép lập trình viên mã hóa chuỗi văn bản thành định dạng nhị phân (byte), thường được sử dụng để chuyển đổi các chuỗi thành dạng có thể gửi qua mạng hoặc lưu trữ trong các định dạng tệp khác nhau.

## Tài liệu
### Mục đích
`TextEncoder` cung cấp một cách đơn giản và hiệu quả để chuyển đổi chuỗi ký tự (string) thành mảng các byte (Uint8Array). Điều này rất hữu ích trong các tình huống như khi bạn cần gửi dữ liệu văn bản qua giao thức mạng hoặc khi bạn muốn lưu trữ văn bản trong các định dạng nhị phân.

### Cú pháp
```javascript
const encoder = new TextEncoder(encoding);
const byteArray = encoder.encode(string);
```

- **encoding**: (Tùy chọn) Một chuỗi xác định bộ mã ký tự (character encoding) được sử dụng, mặc định là `utf-8`.
- **string**: Chuỗi văn bản cần mã hóa.

### Chi tiết
- `TextEncoder` là một phần của Web API và có sẵn trong các trình duyệt hiện đại.
- Phương thức `encode()` trả về một đối tượng `Uint8Array` chứa các byte tương ứng với chuỗi văn bản đầu vào.
- `TextEncoder` hỗ trợ mã hóa UTF-8, UTF-16 và UTF-32.

## Ví dụ
### Ví dụ 1: Mã hóa chuỗi đơn giản
```javascript
const encoder = new TextEncoder();
const byteArray = encoder.encode("Hello, world!");
console.log(byteArray); // Uint8Array(13) [72, 101, 108, 108, 111, 44, 32, 119, 111, 114, 108, 100, 33]
```

### Ví dụ 2: Mã hóa chuỗi với mã hóa cụ thể
```javascript
const encoder = new TextEncoder('utf-16');
const byteArray = encoder.encode("Xin chào");
console.log(byteArray); // Uint8Array chứa mã nhị phân của "Xin chào"
```

## Giải thích
- **Lưu ý về bộ mã hóa**: Mặc định, `TextEncoder` sử dụng UTF-8. Nếu bạn cần mã hóa khác, hãy chỉ định bộ mã hóa phù hợp.
- **Đối tượng trả về**: `Uint8Array` là một mảng chứa các byte, có thể được sử dụng trong các thao tác nhị phân khác.
- **Không hỗ trợ các ký tự không hợp lệ**: Nếu chuỗi chứa ký tự không hợp lệ cho bộ mã hóa đã chọn, `TextEncoder` sẽ ném ra một lỗi.

## Tóm tắt một dòng
`TextEncoder` trong JavaScript là một API dùng để mã hóa chuỗi văn bản thành định dạng nhị phân, giúp xử lý và truyền tải dữ liệu văn bản một cách hiệu quả.