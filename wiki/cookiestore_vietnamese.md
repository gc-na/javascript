<!--
Meta Description: # CookieStore trong JavaScript: Quản lý Cookie Dễ Dàng và Hiệu Quả ## Tóm tắt CookieStore là một API trong JavaScript cho phép lập trình viên quản lý ...
Meta Keywords: cookie, cookiestore, javascript, trong, một
-->

# CookieStore trong JavaScript: Quản lý Cookie Dễ Dàng và Hiệu Quả

## Tóm tắt
CookieStore là một API trong JavaScript cho phép lập trình viên quản lý cookie một cách dễ dàng và hiệu quả. Nó cung cấp các phương thức để tạo, đọc, và xóa cookie trong trình duyệt.

## Tài liệu
### Mục đích
CookieStore được thiết kế nhằm đơn giản hóa việc làm việc với cookie trong JavaScript. Nó giúp lập trình viên có thể thêm, lấy và xóa cookie mà không cần phải thao tác trực tiếp với `document.cookie`.

### Cách sử dụng
API CookieStore có các phương thức chính sau:
- `get(name: string)`: Lấy cookie theo tên.
- `set(cookie: Cookie): Promise<void>`: Thiết lập một cookie mới.
- `delete(name: string): Promise<void>`: Xóa cookie theo tên.

### Chi tiết
CookieStore hỗ trợ các kiểu cookie như:
- `HttpOnly`: Không thể truy cập từ JavaScript.
- `Secure`: Chỉ gửi cookie qua kết nối HTTPS.
- `SameSite`: Kiểm soát cách cookie được gửi trong các yêu cầu giữa các trang.

Để sử dụng CookieStore, bạn cần đảm bảo trình duyệt hỗ trợ API này. Nếu không, bạn có thể sử dụng `document.cookie` như một phương pháp thay thế.

## Ví dụ
### Ví dụ 1: Thiết lập cookie
```javascript
const cookie = {
  name: 'user',
  value: 'John Doe',
  expires: new Date(Date.now() + 3600 * 1000), // Hết hạn sau 1 giờ
};

CookieStore.set(cookie).then(() => {
  console.log('Cookie đã được thiết lập!');
});
```

### Ví dụ 2: Lấy cookie
```javascript
CookieStore.get('user').then(cookie => {
  console.log('Cookie:', cookie);
}).catch(error => {
  console.error('Lỗi khi lấy cookie:', error);
});
```

### Ví dụ 3: Xóa cookie
```javascript
CookieStore.delete('user').then(() => {
  console.log('Cookie đã được xóa!');
}).catch(error => {
  console.error('Lỗi khi xóa cookie:', error);
});
```

## Giải thích
### Những vấn đề thường gặp
- **Hỗ trợ trình duyệt**: Hiện tại, không phải tất cả các trình duyệt đều hỗ trợ CookieStore. Trước khi sử dụng, hãy kiểm tra tính tương thích.
- **CORS và SameSite**: Khi làm việc với cookie, bạn cần chú ý đến chính sách CORS và thuộc tính SameSite, vì điều này có thể ảnh hưởng đến cách cookie được gửi và nhận.
- **Quản lý thời gian sống của cookie**: Đảm bảo thiết lập thời gian hết hạn hợp lý để cookie không bị xóa một cách không mong muốn.

## Tóm tắt một dòng
CookieStore trong JavaScript cung cấp một cách tiếp cận hiện đại và dễ dàng để quản lý cookie trong ứng dụng web.