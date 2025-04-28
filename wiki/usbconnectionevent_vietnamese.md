<!--
Meta Description: # Sự kiện USBConnectionEvent trong JavaScript: Cách quản lý kết nối USB ## Tóm tắt Sự kiện USBConnectionEvent trong JavaScript cho phép các nhà phát t...
Meta Keywords: usb, kết, nối, kiện, thiết
-->

# Sự kiện USBConnectionEvent trong JavaScript: Cách quản lý kết nối USB

## Tóm tắt
Sự kiện USBConnectionEvent trong JavaScript cho phép các nhà phát triển ứng dụng web tương tác với các thiết bị USB được kết nối, giúp nhận biết và xử lý các kết nối hoặc ngắt kết nối thiết bị USB một cách dễ dàng và hiệu quả.

## Tài liệu
### Mục đích
USBConnectionEvent là một sự kiện trong API Web USB, cho phép ứng dụng web nhận thông tin về trạng thái kết nối của các thiết bị USB. Sự kiện này rất hữu ích trong các ứng dụng cần tương tác với phần cứng ngoài, chẳng hạn như máy in, máy quét, hoặc các thiết bị IoT.

### Cách sử dụng
Để sử dụng USBConnectionEvent, trước tiên bạn cần đảm bảo rằng trình duyệt hỗ trợ API Web USB. Sau đó, bạn có thể lắng nghe sự kiện `connect` và `disconnect` để xử lý các thay đổi trạng thái của thiết bị USB.

### Chi tiết
- **Khởi tạo sự kiện**: Khi một thiết bị USB được kết nối hoặc ngắt kết nối, trình duyệt sẽ phát ra một USBConnectionEvent.
- **Thuộc tính**:
  - `device`: Trả về đối tượng thiết bị USB liên quan đến sự kiện.
  - `timeStamp`: Thời gian xảy ra sự kiện.
  
### Cú pháp
```javascript
navigator.usb.addEventListener('connect', (event) => {
    console.log('Device connected:', event.device);
});

navigator.usb.addEventListener('disconnect', (event) => {
    console.log('Device disconnected:', event.device);
});
```

## Ví dụ
### Ví dụ 1: Lắng nghe sự kiện kết nối USB
```javascript
navigator.usb.addEventListener('connect', (event) => {
    alert(`Thiết bị kết nối: ${event.device.productName}`);
});
```

### Ví dụ 2: Lắng nghe sự kiện ngắt kết nối USB
```javascript
navigator.usb.addEventListener('disconnect', (event) => {
    alert(`Thiết bị ngắt kết nối: ${event.device.productName}`);
});
```

## Giải thích
### Những lưu ý thường gặp
- **Hỗ trợ trình duyệt**: Không phải tất cả các trình duyệt đều hỗ trợ API Web USB. Hãy kiểm tra khả năng tương thích trước khi triển khai.
- **Quyền truy cập**: Người dùng cần phải cấp quyền truy cập cho phép ứng dụng của bạn tương tác với thiết bị USB.
- **Cảnh báo bảo mật**: Sử dụng API này cần phải cẩn thận, vì nó có thể truy cập vào phần cứng nhạy cảm.

## Tóm tắt Một dòng
Sự kiện USBConnectionEvent trong JavaScript cho phép quản lý kết nối và ngắt kết nối của thiết bị USB một cách hiệu quả trong ứng dụng web.