<!--
Meta Description: # EventSource trong JavaScript: Giao tiếp Thời gian Thực với Server ## Tóm Tắt `EventSource` là một API trong JavaScript cho phép các ứng dụng web nhậ...
Meta Keywords: eventsource, server, một, liệu, được
-->

# EventSource trong JavaScript: Giao tiếp Thời gian Thực với Server

## Tóm Tắt
`EventSource` là một API trong JavaScript cho phép các ứng dụng web nhận dữ liệu từ server theo thời gian thực thông qua giao thức HTTP. Điều này rất hữu ích trong việc cập nhật nội dung động mà không cần tải lại trang.

## Tài Liệu
### Mục Đích
`EventSource` được sử dụng để thiết lập một kết nối một chiều từ server đến client, cho phép server gửi các sự kiện đến client một cách liên tục. Đây là một phần của tiêu chuẩn SSE (Server-Sent Events).

### Cách Sử Dụng
Để sử dụng `EventSource`, bạn cần tạo một đối tượng `EventSource` với URL của endpoint mà server sẽ gửi sự kiện đến. Dưới đây là cú pháp cơ bản:

```javascript
const eventSource = new EventSource(url);
```

### Các Tham Số
- `url`: Đây là đường dẫn tới endpoint trên server mà bạn muốn nhận sự kiện.

### Các Sự Kiện Quan Trọng
- `onmessage`: Sự kiện này được kích hoạt khi nhận được một thông điệp từ server.
- `onerror`: Sự kiện này được kích hoạt khi có lỗi xảy ra trong quá trình kết nối.

## Ví Dụ
### Ví dụ Cơ Bản
Dưới đây là một ví dụ cơ bản về cách sử dụng `EventSource`:

```javascript
const eventSource = new EventSource('https://example.com/events');

eventSource.onmessage = function(event) {
    console.log('Dữ liệu nhận được:', event.data);
};

eventSource.onerror = function(err) {
    console.error('Lỗi kết nối:', err);
};
```

### Ví dụ với Dữ Liệu JSON
Nếu server gửi dữ liệu ở định dạng JSON, bạn có thể xử lý như sau:

```javascript
const eventSource = new EventSource('https://example.com/json-events');

eventSource.onmessage = function(event) {
    const data = JSON.parse(event.data);
    console.log('Dữ liệu JSON nhận được:', data);
};
```

## Giải Thích
### Những Cạm Bẫy Thường Gặp
- **Chỉ hỗ trợ một chiều**: `EventSource` chỉ cho phép server gửi dữ liệu đến client. Nếu bạn cần gửi dữ liệu từ client đến server, bạn sẽ cần sử dụng AJAX hoặc WebSocket.
- **Hỗ trợ trình duyệt**: Mặc dù `EventSource` được hỗ trợ trên nhiều trình duyệt, nhưng một số phiên bản cũ có thể không hỗ trợ. Hãy kiểm tra tính tương thích trước khi triển khai.
- **Kết nối tự động**: Nếu kết nối bị gián đoạn, `EventSource` sẽ tự động cố gắng kết nối lại. Điều này có thể gây ra vấn đề nếu server không được cấu hình đúng để xử lý nhiều kết nối đồng thời.

## Tóm Tắt Một Dòng
`EventSource` là một API mạnh mẽ trong JavaScript, cho phép nhận dữ liệu từ server theo thời gian thực một cách đơn giản và hiệu quả.