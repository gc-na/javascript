<!--
Meta Description: # ClipboardItem trong JavaScript: Hướng Dẫn Toàn Diện và Ví Dụ Cụ Thể ## Tóm tắt `ClipboardItem` là một giao thức trong JavaScript cho phép các nhà ph...
Meta Keywords: clipboarditem, clipboard, một, sao, chép
-->

# ClipboardItem trong JavaScript: Hướng Dẫn Toàn Diện và Ví Dụ Cụ Thể

## Tóm tắt
`ClipboardItem` là một giao thức trong JavaScript cho phép các nhà phát triển tạo đối tượng để lưu trữ dữ liệu vào clipboard, hỗ trợ việc sao chép và dán dữ liệu đa dạng, bao gồm hình ảnh và văn bản.

## Tài liệu
### Mục đích
`ClipboardItem` được sử dụng để tạo và quản lý các mục trong clipboard, giúp đơn giản hóa việc sao chép và dán dữ liệu từ ứng dụng web.

### Cách sử dụng
Để sử dụng `ClipboardItem`, bạn cần khởi tạo một đối tượng mới với một `Map` chứa các loại MIME và dữ liệu tương ứng. Sau đó, bạn có thể sử dụng phương thức `write` của `Clipboard` để sao chép nó vào clipboard.

#### Cú pháp
```javascript
let clipboardItem = new ClipboardItem({
  'image/png': new Blob([imageData], { type: 'image/png' }),
  'text/plain': new Blob(['Nội dung văn bản'], { type: 'text/plain' })
});
```

### Chi tiết
- **Tham số**: Đối số đầu vào của `ClipboardItem` là một `Map` với các khóa là loại MIME (ví dụ: `'image/png'`, `'text/plain'`) và giá trị là các đối tượng `Blob`.
- **Phương thức**: Để lưu một `ClipboardItem` vào clipboard, bạn cần sử dụng phương thức `navigator.clipboard.write()`:
```javascript
navigator.clipboard.write([clipboardItem]).then(function() {
  console.log('Sao chép thành công!');
}).catch(function(error) {
  console.error('Lỗi khi sao chép:', error);
});
```

## Ví dụ
### Ví dụ Cơ Bản
```javascript
// Tạo một ClipboardItem với hình ảnh và văn bản
const imageBlob = new Blob([/* dữ liệu nhị phân hình ảnh */], { type: 'image/png' });
const textBlob = new Blob(['Đây là một văn bản'], { type: 'text/plain' });

const clipboardItem = new ClipboardItem({
  'image/png': imageBlob,
  'text/plain': textBlob
});

// Sao chép vào clipboard
navigator.clipboard.write([clipboardItem])
  .then(() => console.log('Dữ liệu đã được sao chép thành công!'))
  .catch(err => console.error('Lỗi khi sao chép:', err));
```

## Giải thích
### Những điểm cần lưu ý
- **Hỗ trợ trình duyệt**: Hiện tại, `ClipboardItem` có thể không được hỗ trợ bởi tất cả các trình duyệt. Kiểm tra tính tương thích trước khi sử dụng.
- **Quyền truy cập clipboard**: Để sử dụng clipboard, trang web phải được phục vụ qua HTTPS hoặc localhost.
- **Blob**: Đảm bảo rằng các đối tượng `Blob` được tạo ra đúng cách với kiểu MIME chính xác.

## Tóm tắt một dòng
`ClipboardItem` trong JavaScript là một công cụ hữu ích cho việc quản lý và sao chép dữ liệu đa dạng vào clipboard, hỗ trợ các loại MIME khác nhau.