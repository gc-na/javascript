<!--
Meta Description: # Sự Kiện `onclose` trong JavaScript: Cách Thức và Ứng Dụng ## Tóm tắt Sự kiện `onclose` trong JavaScript được sử dụng để xử lý các tình huống khi một...
Meta Keywords: kết, nối, kiện, websocket, đóng
-->

# Sự Kiện `onclose` trong JavaScript: Cách Thức và Ứng Dụng

## Tóm tắt
Sự kiện `onclose` trong JavaScript được sử dụng để xử lý các tình huống khi một kết nối WebSocket hoặc một cửa sổ trình duyệt bị đóng. Sự kiện này giúp lập trình viên nắm bắt và quản lý các hành động cần thiết khi một kết nối không còn hoạt động.

## Tài liệu
### Mục đích
Sự kiện `onclose` cho phép lập trình viên theo dõi trạng thái của kết nối WebSocket hoặc cửa sổ trình duyệt. Khi sự kiện này xảy ra, lập trình viên có thể thực hiện các hành động như thông báo cho người dùng, thực hiện các thao tác dọn dẹp, hoặc cố gắng tái kết nối.

### Cách sử dụng
Sự kiện `onclose` thường được gán trực tiếp vào đối tượng WebSocket hoặc cửa sổ. Cú pháp cơ bản như sau:

```javascript
webSocket.onclose = function(event) {
    // Xử lý sự kiện khi kết nối bị đóng
};
```

### Chi tiết
- **Đối tượng sự kiện**: Tham số `event` chứa thông tin về sự kiện đóng, như mã trạng thái và lý do kết thúc.
- **Mã trạng thái**: Sử dụng `event.code` để biết lý do kết thúc kết nối.
- **Lý do đóng**: `event.reason` có thể cung cấp thêm thông tin về lý do kết nối bị đóng (nếu có).

## Ví dụ
### Ví dụ 1: Xử lý sự kiện `onclose` với WebSocket
```javascript
const webSocket = new WebSocket('ws://example.com/socket');

webSocket.onclose = function(event) {
    console.log('Kết nối đã đóng', event.code, event.reason);
};
```

### Ví dụ 2: Cố gắng tái kết nối khi kết nối đóng
```javascript
function connect() {
    const webSocket = new WebSocket('ws://example.com/socket');

    webSocket.onclose = function(event) {
        console.log('Kết nối đã đóng, cố gắng tái kết nối...');
        setTimeout(connect, 1000); // Tái kết nối sau 1 giây
    };
}

connect();
```

## Giải thích
### Những điểm thường gặp
- **Không xử lý sự kiện**: Nếu không gán `onclose`, bạn sẽ không nhận được thông báo khi kết nối bị đóng.
- **Kết nối đóng không mong muốn**: Có thể xảy ra các tình huống như mất kết nối mạng hoặc server dừng hoạt động. Hãy chuẩn bị cho các xử lý tái kết nối.
- **Mã trạng thái không rõ ràng**: Đôi khi, mã trạng thái không cung cấp thông tin rõ ràng về lý do kết thúc. Nên kết hợp các biện pháp khác để xác định nguyên nhân.

## Tóm tắt một dòng
Sự kiện `onclose` trong JavaScript giúp lập trình viên quản lý và xử lý các tình huống khi kết nối WebSocket hoặc cửa sổ bị đóng.