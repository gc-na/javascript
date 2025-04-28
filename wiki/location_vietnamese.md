<!--
Meta Description: # Đối tượng location trong JavaScript: Hướng dẫn chi tiết ## Tóm tắt Đối tượng `location` trong JavaScript cho phép truy cập và thao tác với URL của t...
Meta Keywords: location, url, của, đối, tượng
-->

# Đối tượng location trong JavaScript: Hướng dẫn chi tiết

## Tóm tắt
Đối tượng `location` trong JavaScript cho phép truy cập và thao tác với URL của tài liệu hiện tại. Nó hữu ích cho việc điều hướng, lấy thông tin URL và thay đổi địa chỉ trang web.

## Tài liệu
### Mục đích
Đối tượng `location` là một phần của đối tượng `window` trong JavaScript, cung cấp thông tin chi tiết về URL hiện tại. Nó cho phép lập trình viên truy cập các thành phần của URL như tên miền, đường dẫn, truy vấn và phân đoạn, cũng như cho phép điều hướng đến các URL khác.

### Cách sử dụng
Đối tượng `location` có thể được sử dụng như sau:
- `location.href`: Trả về hoặc thiết lập URL hiện tại.
- `location.protocol`: Trả về giao thức của URL (ví dụ: `http:` hoặc `https:`).
- `location.host`: Trả về tên miền và số cổng (nếu có) của URL.
- `location.pathname`: Trả về đường dẫn của URL.
- `location.search`: Trả về chuỗi truy vấn (query string) của URL.
- `location.hash`: Trả về phần phân đoạn (fragment) của URL.
- `location.assign()`: Chuyển hướng đến một URL mới.
- `location.reload()`: Tải lại tài liệu hiện tại.

## Ví dụ
Dưới đây là một số ví dụ cơ bản về cách sử dụng đối tượng `location`:

```javascript
// Lấy URL hiện tại
console.log(location.href);

// Chuyển hướng đến một URL mới
location.href = 'https://www.example.com';

// Lấy giao thức của URL
console.log(location.protocol); // Ví dụ: "https:"

// Lấy đường dẫn của URL
console.log(location.pathname); // Ví dụ: "/path/to/page"

// Lấy chuỗi truy vấn của URL
console.log(location.search); // Ví dụ: "?query=123"

// Tải lại trang hiện tại
location.reload();
```

## Giải thích
Mặc dù đối tượng `location` rất mạnh mẽ, nhưng có một số lưu ý cần nhớ:
- Việc thay đổi `location.href` sẽ dẫn đến chuyển hướng đến URL mới, và mọi thay đổi trên trang hiện tại sẽ bị mất.
- Sử dụng `location.reload()` có thể gây ra vấn đề về hiệu suất nếu sử dụng không đúng cách, đặc biệt là trong các ứng dụng lớn.
- Một số trình duyệt có thể xử lý các thay đổi `location` khác nhau, vì vậy cần kiểm tra tính tương thích khi sử dụng các thuộc tính và phương thức của đối tượng `location`.

## Tóm tắt một câu
Đối tượng `location` trong JavaScript cung cấp thông tin và phương thức cần thiết để thao tác với URL của tài liệu hiện tại, giúp dễ dàng điều hướng và lấy thông tin URL.