<!--
Meta Description: # XMLHttpRequestEventTarget trong JavaScript: Hướng dẫn Chi Tiết ## Tóm tắt XMLHttpRequestEventTarget là một đối tượng trong JavaScript cho phép bạn t...
Meta Keywords: kiện, yêu, cầu, xhr, các
-->

# XMLHttpRequestEventTarget trong JavaScript: Hướng dẫn Chi Tiết

## Tóm tắt
XMLHttpRequestEventTarget là một đối tượng trong JavaScript cho phép bạn theo dõi và xử lý các sự kiện liên quan đến yêu cầu HTTP được thực hiện bằng đối tượng XMLHttpRequest. Điều này giúp lập trình viên dễ dàng quản lý trạng thái và phản hồi của các yêu cầu mạng.

## Tài liệu
### Mục đích
XMLHttpRequestEventTarget cung cấp các phương thức và thuộc tính để xử lý các sự kiện như `load`, `error`, và `abort` khi làm việc với XMLHttpRequest. Nó cho phép bạn thêm các trình xử lý sự kiện cho các sự kiện này, giúp việc quản lý yêu cầu mạng trở nên linh hoạt và hiệu quả hơn.

### Cách sử dụng
Để sử dụng XMLHttpRequestEventTarget, bạn cần tạo một đối tượng XMLHttpRequest và thêm các trình xử lý sự kiện cho các sự kiện mà bạn muốn theo dõi. Dưới đây là cú pháp cơ bản:

```javascript
var xhr = new XMLHttpRequest();

// Thêm trình xử lý sự kiện
xhr.addEventListener('load', function() {
    console.log('Yêu cầu đã hoàn thành:', xhr.responseText);
});

xhr.addEventListener('error', function() {
    console.error('Có lỗi xảy ra trong khi thực hiện yêu cầu.');
});

// Mở và gửi yêu cầu
xhr.open('GET', 'https://api.example.com/data');
xhr.send();
```

### Chi tiết
- **Các sự kiện hỗ trợ**: XMLHttpRequestEventTarget hỗ trợ nhiều sự kiện, bao gồm:
  - `load`: Khi yêu cầu hoàn thành thành công.
  - `error`: Khi có lỗi xảy ra trong quá trình thực hiện yêu cầu.
  - `abort`: Khi yêu cầu bị hủy.

- **Phương thức**:
  - `addEventListener(type, listener)`: Thêm một trình xử lý sự kiện cho một sự kiện cụ thể.
  - `removeEventListener(type, listener)`: Gỡ bỏ một trình xử lý sự kiện đã đăng ký.

- **Thuộc tính**:
  - `readyState`: Trạng thái hiện tại của yêu cầu.
  - `status`: Mã trạng thái HTTP của phản hồi.

## Ví dụ
### Ví dụ 1: Theo dõi sự kiện load
```javascript
var xhr = new XMLHttpRequest();
xhr.open('GET', 'https://api.example.com/data');

xhr.addEventListener('load', function() {
    console.log('Dữ liệu nhận được:', xhr.responseText);
});
xhr.send();
```

### Ví dụ 2: Theo dõi sự kiện error
```javascript
var xhr = new XMLHttpRequest();
xhr.open('GET', 'https://api.example.com/invalid-url');

xhr.addEventListener('error', function() {
    console.error('Yêu cầu đã thất bại.');
});
xhr.send();
```

## Giải thích
1. **Cần chú ý đến trạng thái của yêu cầu**: Trạng thái của yêu cầu có thể thay đổi nhanh chóng. Đừng quên kiểm tra `readyState` trước khi xử lý dữ liệu trong sự kiện `load`.
2. **Cấu hình CORS**: Nếu bạn thực hiện yêu cầu đến một miền khác, hãy chắc chắn rằng server hỗ trợ CORS (Cross-Origin Resource Sharing).
3. **Lỗi mạng**: Các sự kiện `error` không chỉ xảy ra khi có lỗi từ server mà còn có thể xảy ra khi không có kết nối mạng.

## Tóm tắt một dòng
XMLHttpRequestEventTarget trong JavaScript là một công cụ mạnh mẽ để theo dõi và quản lý các sự kiện của yêu cầu HTTP.