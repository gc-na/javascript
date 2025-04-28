<!--
Meta Description: # encodeURI trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ ## Tóm Tắt `encodeURI` là một hàm trong JavaScript được sử dụng để mã hóa một chuỗi URI (Uni...
Meta Keywords: uri, hóa, encodeuri, một, các
-->

# encodeURI trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ

## Tóm Tắt
`encodeURI` là một hàm trong JavaScript được sử dụng để mã hóa một chuỗi URI (Uniform Resource Identifier) bằng cách chuyển đổi các ký tự đặc biệt thành các mã định dạng URL phù hợp.

## Tài Liệu
Hàm `encodeURI` có mục đích chính là mã hóa một chuỗi URI, giúp đảm bảo rằng các ký tự đặc biệt không làm hỏng cấu trúc của URI. Các ký tự như dấu cách, dấu hỏi, dấu # và một số ký tự khác sẽ được chuyển đổi thành dạng mã hóa URL, tức là các ký tự này sẽ được thay thế bằng ký tự % theo sau là mã thập lục phân tương ứng.

### Cú Pháp
```javascript
encodeURI(uri)
```

### Tham Số
- `uri`: Một chuỗi chứa URI mà bạn muốn mã hóa.

### Giá Trị Trả Về
- Hàm trả về một chuỗi đã được mã hóa URI.

### Lưu Ý
- `encodeURI` không mã hóa các ký tự đã được định nghĩa trong URI như `:`, `/`, `?`, `&`, và `#`, vì chúng có ý nghĩa đặc biệt trong URI.

## Ví Dụ
### Ví Dụ 1: Mã Hóa Một URI Đơn Giản
```javascript
const uri = "https://example.com/hello world";
const encodedURI = encodeURI(uri);
console.log(encodedURI); // Kết quả: https://example.com/hello%20world
```

### Ví Dụ 2: Mã Hóa Một URI Có Ký Tự Đặc Biệt
```javascript
const uri = "https://example.com/search?query=JavaScript & CSS";
const encodedURI = encodeURI(uri);
console.log(encodedURI); // Kết quả: https://example.com/search?query=JavaScript%20%26%20CSS
```

## Giải Thích
Một số vấn đề phổ biến khi sử dụng `encodeURI` bao gồm:

- **Không mã hóa các ký tự đặc biệt:** Như đã đề cập, `encodeURI` không mã hóa các ký tự có ý nghĩa trong URI, điều này có thể gây ra lỗi nếu bạn không chú ý. Nếu cần mã hóa các ký tự này, bạn nên sử dụng hàm `encodeURIComponent`.
  
- **Sử dụng không đúng:** Nhiều lập trình viên mới có thể không nhận ra sự khác biệt giữa `encodeURI` và `encodeURIComponent`, dẫn đến việc mã hóa không đúng cần thiết cho từng trường hợp.

### Ghi Chú
- `encodeURI` rất hữu ích khi bạn cần chuẩn bị một URI cho việc truyền tải qua mạng hoặc khi tạo các liên kết động trong ứng dụng web.

## Tóm Tắt Một Dòng
Hàm `encodeURI` trong JavaScript được sử dụng để mã hóa một chuỗi URI, chuyển đổi các ký tự đặc biệt thành định dạng URL an toàn.