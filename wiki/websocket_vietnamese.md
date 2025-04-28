<!--
Meta Description: # WebSocket trong JavaScript: Giao tiếp thời gian thực cho ứng dụng web ## Tóm tắt WebSocket là một giao thức mạng cho phép giao tiếp hai chiều giữa s...
Meta Keywords: websocket, kết, nối, socket, một
-->

# WebSocket trong JavaScript: Giao tiếp thời gian thực cho ứng dụng web

## Tóm tắt
WebSocket là một giao thức mạng cho phép giao tiếp hai chiều giữa server và client qua một kết nối TCP duy nhất. Trong JavaScript, WebSocket cung cấp một API đơn giản và hiệu quả để phát triển các ứng dụng web thời gian thực, như chat, thông báo và cập nhật dữ liệu trực tiếp.

## Tài liệu
### Mục đích
WebSocket được thiết kế để tạo ra một kết nối liên tục giữa client và server, cho phép gửi và nhận dữ liệu mà không cần phải thực hiện lại các yêu cầu HTTP truyền thống. Điều này giúp giảm độ trễ và tăng hiệu suất cho các ứng dụng yêu cầu cập nhật dữ liệu thường xuyên.

### Cách sử dụng
1. **Khởi tạo WebSocket**: Để bắt đầu sử dụng WebSocket, bạn cần tạo một đối tượng WebSocket với URL của server.
   ```javascript
   const socket = new WebSocket('ws://example.com/socket');
   ```

2. **Sự kiện**: WebSocket hỗ trợ một số sự kiện chính:
   - `onopen`: Xảy ra khi kết nối được thiết lập thành công.
   - `onmessage`: Xảy ra khi nhận được tin nhắn từ server.
   - `onerror`: Xảy ra khi có lỗi xảy ra.
   - `onclose`: Xảy ra khi kết nối bị đóng.

3. **Gửi dữ liệu**: Để gửi dữ liệu từ client tới server, sử dụng phương thức `send`.
   ```javascript
   socket.send('Hello Server!');
   ```

4. **Đóng kết nối**: Khi không còn sử dụng, đóng kết nối bằng phương thức `close`.
   ```javascript
   socket.close();
   ```

### Chi tiết
WebSocket sử dụng một cơ chế handshake để tạo kết nối ban đầu. Sau khi kết nối được thiết lập, client và server có thể truyền tải dữ liệu qua lại một cách hiệu quả. WebSocket hỗ trợ cả văn bản và nhị phân, cho phép truyền tải nhiều loại dữ liệu khác nhau.

## Ví dụ
### Ví dụ cơ bản
```javascript
const socket = new WebSocket('ws://example.com/socket');

socket.onopen = function(event) {
    console.log('Kết nối đã được thiết lập.');
    socket.send('Xin chào từ client!');
};

socket.onmessage = function(event) {
    console.log('Tin nhắn từ server:', event.data);
};

socket.onerror = function(event) {
    console.error('Lỗi:', event);
};

socket.onclose = function(event) {
    console.log('Kết nối đã đóng:', event);
};
```

### Ví dụ gửi và nhận dữ liệu nhị phân
```javascript
const socket = new WebSocket('ws://example.com/socket');
const arrayBuffer = new Uint8Array([1, 2, 3]);

socket.onopen = function() {
    socket.send(arrayBuffer);
};

socket.onmessage = function(event) {
    console.log('Nhận dữ liệu nhị phân:', event.data);
};
```

## Giải thích
### Cạm bẫy thường gặp
- **Lỗi kết nối**: Đảm bảo rằng URL của WebSocket là chính xác và server đang lắng nghe kết nối.
- **Không xử lý các sự kiện**: Quên không xử lý các sự kiện như `onerror` có thể dẫn đến việc không phát hiện được lỗi.
- **Đóng kết nối không đúng cách**: Đảm bảo rằng bạn đóng kết nối khi không còn sử dụng để giải phóng tài nguyên.

### Ghi chú thêm
- WebSocket hỗ trợ các subprotocols, cho phép client và server thống nhất về cách thức giao tiếp.
- Hãy luôn kiểm tra độ bảo mật khi sử dụng WebSocket, đặc biệt là với kết nối không an toàn (ws://).

## Tóm tắt một dòng
WebSocket trong JavaScript cung cấp một phương thức hiệu quả để giao tiếp thời gian thực giữa client và server thông qua một kết nối TCP duy nhất.