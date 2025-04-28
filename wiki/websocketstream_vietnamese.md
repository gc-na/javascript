<!--
Meta Description: # WebSocketStream: Khám Phá Giao Thức WebSocket Trong JavaScript ## Tóm tắt WebSocketStream là một giao thức trong JavaScript cho phép truyền tải dữ l...
Meta Keywords: kết, nối, socket, websocket, liệu
-->

# WebSocketStream: Khám Phá Giao Thức WebSocket Trong JavaScript

## Tóm tắt
WebSocketStream là một giao thức trong JavaScript cho phép truyền tải dữ liệu hai chiều giữa máy khách và máy chủ qua kết nối WebSocket, giúp cải thiện hiệu suất và hiệu quả trong các ứng dụng web thời gian thực.

## Tài liệu
### Mục đích
WebSocketStream được thiết kế để cung cấp một phương thức giao tiếp hiệu quả giữa trình duyệt và máy chủ. Khác với HTTP, WebSocket cho phép duy trì một kết nối mở, cho phép dữ liệu được gửi và nhận liên tục mà không cần phải tái thiết lập kết nối.

### Cách sử dụng
Để sử dụng WebSocketStream trong JavaScript, bạn cần thực hiện các bước sau:

1. **Khởi tạo kết nối**
   ```javascript
   const socket = new WebSocket('ws://example.com/socket');
   ```

2. **Xử lý sự kiện**
   Bạn có thể sử dụng các sự kiện như `onopen`, `onmessage`, `onerror`, và `onclose` để xử lý các tình huống khác nhau của kết nối.
   ```javascript
   socket.onopen = function(event) {
       console.log('Kết nối đã được mở!');
   };

   socket.onmessage = function(event) {
       console.log('Dữ liệu nhận được: ', event.data);
   };

   socket.onerror = function(error) {
       console.error('Lỗi WebSocket: ', error);
   };

   socket.onclose = function(event) {
       console.log('Kết nối đã đóng: ', event);
   };
   ```

3. **Gửi dữ liệu**
   Để gửi dữ liệu qua WebSocket, bạn sử dụng phương thức `send()`.
   ```javascript
   socket.send('Xin chào từ máy khách!');
   ```

### Chi tiết
- **Kết nối mở**: Khi kết nối WebSocket được mở, bạn có thể gửi và nhận dữ liệu mà không cần phải thiết lập lại kết nối.
- **Phản hồi**: Dữ liệu nhận được từ máy chủ được xử lý trong hàm `onmessage`.
- **Đóng kết nối**: Kết nối có thể được đóng từ cả hai phía (máy khách hoặc máy chủ) bằng cách gọi `close()`.

## Ví dụ
### Ví dụ 1: Kết nối đơn giản
```javascript
const socket = new WebSocket('ws://example.com/socket');

socket.onopen = function() {
    console.log('Kết nối đã mở!');
    socket.send('Xin chào');
};

socket.onmessage = function(event) {
    console.log('Nhận: ', event.data);
};
```

### Ví dụ 2: Xử lý lỗi
```javascript
const socket = new WebSocket('ws://example.com/socket');

socket.onerror = function(error) {
    console.error('Lỗi: ', error.message);
};
```

## Giải thích
Khi làm việc với WebSocketStream, có một số vấn đề cần chú ý:
- **Kết nối không ổn định**: Kết nối WebSocket có thể bị mất do nhiều lý do (mạng không ổn định, máy chủ không phản hồi, v.v.). Cần có biện pháp để tự động kết nối lại.
- **Bảo mật**: Sử dụng WebSocket qua HTTPS (wss://) để bảo vệ dữ liệu truyền tải khỏi những kẻ tấn công.
- **Quản lý dữ liệu**: Đảm bảo rằng dữ liệu được gửi và nhận đúng định dạng và loại.

## Tóm tắt một dòng
WebSocketStream trong JavaScript cho phép giao tiếp hai chiều hiệu quả qua kết nối mở, lý tưởng cho các ứng dụng web thời gian thực.