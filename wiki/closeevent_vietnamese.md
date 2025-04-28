<!--
Meta Description: # CloseEvent trong JavaScript: Hiểu Biết và Ứng Dụng ## Tóm tắt CloseEvent là một sự kiện trong JavaScript, được kích hoạt khi một kết nối WebSocket h...
Meta Keywords: một, kết, nối, closeevent, đóng
-->

# CloseEvent trong JavaScript: Hiểu Biết và Ứng Dụng

## Tóm tắt
CloseEvent là một sự kiện trong JavaScript, được kích hoạt khi một kết nối WebSocket hoặc một cửa sổ trình duyệt bị đóng. Bài viết này sẽ cung cấp cái nhìn tổng quan về CloseEvent, cách sử dụng và các ví dụ minh họa.

## Tài liệu
CloseEvent là một sự kiện được sử dụng trong ngữ cảnh WebSocket và một số API khác trong trình duyệt. Sự kiện này cho phép lập trình viên xác định khi một kết nối đã bị đóng và thu thập thông tin về lý do đóng kết nối đó.

### Mục đích
Mục đích chính của CloseEvent là giúp lập trình viên xử lý tình huống khi một kết nối hoặc một cửa sổ bị đóng, từ đó có thể thực hiện các hành động thích hợp như thông báo cho người dùng hoặc cố gắng kết nối lại.

### Cách sử dụng
CloseEvent thường được sử dụng trong các trình xử lý sự kiện. Để sử dụng CloseEvent, bạn cần lắng nghe sự kiện `close` trên đối tượng WebSocket. 

```javascript
const socket = new WebSocket('ws://example.com/socket');

// Lắng nghe sự kiện close
socket.addEventListener('close', function(event) {
    console.log('Kết nối đã đóng:', event.code, event.reason);
});
```

### Chi tiết
CloseEvent có một số thuộc tính quan trọng:
- `code`: Mã số trạng thái (từ 1000 đến 4999) cho biết lý do kết nối bị đóng.
- `reason`: Một chuỗi mô tả lý do mà kết nối đã bị đóng.
- `wasClean`: Một boolean chỉ định liệu kết nối đã được đóng một cách hợp lệ hay không.

## Ví dụ
Dưới đây là ví dụ đơn giản về cách sử dụng CloseEvent với WebSocket.

```javascript
const socket = new WebSocket('ws://example.com/socket');

socket.addEventListener('open', function(event) {
    console.log('Kết nối đã mở');
});

// Xử lý sự kiện close
socket.addEventListener('close', function(event) {
    console.log('Kết nối đã đóng với mã:', event.code);
    console.log('Lý do:', event.reason);
});

// Đóng kết nối
socket.close(1000, 'Hoàn thành phiên làm việc');
```

## Giải thích
Khi làm việc với CloseEvent, có một số điểm cần lưu ý:
- Mã trạng thái (code) từ 1000 đến 4999 là các mã tiêu chuẩn được sử dụng để mô tả lý do đóng kết nối. Bạn nên sử dụng các mã này để đảm bảo tính tương thích.
- Không phải tất cả các trình duyệt đều hỗ trợ CloseEvent một cách giống nhau, vì vậy bạn cần kiểm tra tính tương thích trước khi triển khai.

## Tóm tắt một câu
CloseEvent trong JavaScript cho phép lập trình viên xử lý các tình huống khi một kết nối hoặc cửa sổ bị đóng, cung cấp thông tin về lý do và trạng thái của sự kiện đó.