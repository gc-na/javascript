<!--
Meta Description: # TextDecoder trong JavaScript: Giải mã chuỗi ký tự từ Buffer ## Tóm tắt `TextDecoder` là một API trong JavaScript cho phép chuyển đổi dữ liệu nhị phâ...
Meta Keywords: textdecoder, một, utf, hóa, giải
-->

# TextDecoder trong JavaScript: Giải mã chuỗi ký tự từ Buffer

## Tóm tắt
`TextDecoder` là một API trong JavaScript cho phép chuyển đổi dữ liệu nhị phân (thường là từ `ArrayBuffer` hoặc `Uint8Array`) thành chuỗi ký tự sử dụng các bộ mã hóa như UTF-8, UTF-16, ISO-8859-1, và nhiều hơn nữa.

## Tài liệu
### Mục đích
`TextDecoder` được sử dụng để giải mã dữ liệu nhị phân thành chuỗi ký tự. Điều này rất hữu ích khi bạn cần xử lý dữ liệu được mã hóa, chẳng hạn như khi nhận dữ liệu từ máy chủ hoặc đọc tệp.

### Cách sử dụng
Để sử dụng `TextDecoder`, bạn cần khởi tạo một đối tượng `TextDecoder` với bộ mã hóa mong muốn. Dưới đây là cú pháp cơ bản:

```javascript
const decoder = new TextDecoder(encoding, options);
```

- **encoding**: Một chuỗi xác định bộ mã hóa (mặc định là "utf-8").
- **options**: Một đối tượng tùy chọn (có thể chứa thuộc tính `fatal` để chỉ định hành vi khi gặp lỗi).

Để giải mã một `ArrayBuffer` hoặc `Uint8Array`, bạn sử dụng phương thức `.decode()`:

```javascript
const string = decoder.decode(uint8Array);
```

### Chi tiết
`TextDecoder` hỗ trợ nhiều bộ mã hóa khác nhau, bao gồm nhưng không giới hạn ở:
- "utf-8"
- "utf-16le"
- "utf-16be"
- "iso-8859-1"

Nếu bộ mã hóa không được hỗ trợ, một `TypeError` sẽ được ném ra. Đối với các tùy chọn, nếu `fatal` được đặt thành `true`, `TextDecoder` sẽ ném một lỗi khi gặp ký tự không hợp lệ.

## Ví dụ
Dưới đây là một ví dụ đơn giản về cách sử dụng `TextDecoder` để giải mã một mảng byte thành chuỗi:

```javascript
// Giả sử bạn có một Uint8Array chứa dữ liệu nhị phân
const uint8Array = new Uint8Array([72, 101, 108, 108, 111]); // "Hello" trong UTF-8

// Tạo một TextDecoder với mã hóa UTF-8
const decoder = new TextDecoder('utf-8');

// Giải mã mảng byte thành chuỗi
const decodedString = decoder.decode(uint8Array);

console.log(decodedString); // Kết quả: "Hello"
```

Một ví dụ khác, sử dụng mã hóa UTF-16:

```javascript
const uint8Array = new Uint8Array([0xff, 0xfe, 0x72, 0x00, 0x69, 0x00]); // "ri" trong UTF-16

// Tạo một TextDecoder với mã hóa UTF-16
const decoder = new TextDecoder('utf-16le');

// Giải mã mảng byte thành chuỗi
const decodedString = decoder.decode(uint8Array);

console.log(decodedString); // Kết quả: "ri"
```

## Giải thích
Khi sử dụng `TextDecoder`, bạn nên lưu ý một số điều sau:

- Đảm bảo rằng dữ liệu nhị phân bạn đang cố gắng giải mã thực sự tương ứng với bộ mã hóa đã chỉ định. Nếu không, bạn có thể gặp lỗi hoặc kết quả không mong muốn.
- Nếu bạn làm việc với dữ liệu lớn, hãy cân nhắc về hiệu suất, vì việc giải mã có thể tốn thời gian.
- `TextDecoder` là một phần của Web API, vì vậy nó có thể không khả dụng trong môi trường Node.js mà không có các polyfill hoặc thư viện tương tự.

## Tóm tắt một dòng
`TextDecoder` trong JavaScript là công cụ hữu ích để giải mã dữ liệu nhị phân thành chuỗi ký tự với nhiều bộ mã hóa khác nhau.