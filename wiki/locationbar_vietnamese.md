<!--
Meta Description: # Locationbar trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ Sử Dụng ## Tóm tắt Locationbar là một tính năng trong JavaScript cho phép người phát triển...
Meta Keywords: url, window, location, của, hiện
-->

# Locationbar trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ Sử Dụng

## Tóm tắt
Locationbar là một tính năng trong JavaScript cho phép người phát triển kiểm soát và tương tác với thanh địa chỉ của trình duyệt, giúp quản lý URL và lịch sử duyệt web.

## Tài Liệu
### Mục đích
Locationbar không phải là một đối tượng riêng lẻ trong JavaScript, mà nó thường được nhắc đến trong ngữ cảnh của đối tượng `window.location`. Đối tượng này cho phép lập trình viên truy cập và thay đổi URL hiện tại của trang web, cung cấp khả năng điều hướng và quản lý lịch sử duyệt web.

### Cách sử dụng
- **Truy cập URL hiện tại**: Bạn có thể lấy URL hiện tại thông qua `window.location.href`.
- **Thay đổi URL**: Sử dụng `window.location.assign()` để chuyển hướng đến một URL mới hoặc `window.location.replace()` để thay thế URL hiện tại mà không lưu vào lịch sử duyệt.
- **Lấy thông tin từ URL**: Bạn có thể truy cập từng thành phần của URL (như protocol, host, pathname, search, hash) thông qua các thuộc tính của `window.location`.

### Chi tiết
Đối tượng `window.location` cung cấp các thuộc tính và phương thức sau:
- `window.location.href`: Trả về URL đầy đủ của tài liệu hiện tại.
- `window.location.protocol`: Trả về giao thức của URL (ví dụ: "http:", "https:").
- `window.location.host`: Trả về tên miền và cổng (nếu có).
- `window.location.pathname`: Trả về đường dẫn của tài liệu.
- `window.location.search`: Trả về chuỗi truy vấn (query string).
- `window.location.hash`: Trả về phần băm của URL.
- `window.location.assign(url)`: Chuyển đến URL mới.
- `window.location.replace(url)`: Thay thế URL hiện tại bằng URL mới mà không tạo ra một trang mới trong lịch sử.

## Ví Dụ
### Ví dụ 1: Lấy URL hiện tại
```javascript
console.log(window.location.href); // In ra URL hiện tại
```

### Ví dụ 2: Chuyển hướng đến URL mới
```javascript
window.location.assign("https://www.example.com");
```

### Ví dụ 3: Thay thế URL hiện tại
```javascript
window.location.replace("https://www.example.com");
```

## Giải Thích
- **Cảnh báo**: Khi sử dụng `window.location.replace()`, người dùng sẽ không thể quay lại trang trước đó bằng nút quay lại của trình duyệt, vì vậy hãy sử dụng nó cẩn thận.
- **Trình duyệt không hỗ trợ**: Đảm bảo rằng bạn kiểm tra tính tương thích của các thuộc tính và phương thức với các trình duyệt khác nhau.
- **Lỗi thường gặp**: Một số lập trình viên có thể quên kiểm tra giá trị của `window.location` trước khi thay đổi, dẫn đến lỗi không mong muốn.

## Tóm tắt một dòng
Locationbar trong JavaScript cho phép lập trình viên quản lý và điều hướng URL của trang web thông qua đối tượng `window.location`.