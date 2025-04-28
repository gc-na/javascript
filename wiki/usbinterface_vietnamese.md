<!--
Meta Description: # USBInterface trong JavaScript: Cách sử dụng và ứng dụng ## Tóm tắt USBInterface là một giao diện trong JavaScript cho phép các nhà phát triển tương ...
Meta Keywords: thiết, kết, nối, usb, device
-->

# USBInterface trong JavaScript: Cách sử dụng và ứng dụng

## Tóm tắt
USBInterface là một giao diện trong JavaScript cho phép các nhà phát triển tương tác với các thiết bị USB thông qua API WebUSB, giúp việc kết nối và giao tiếp với các thiết bị ngoại vi trở nên dễ dàng hơn.

## Tài liệu
### Mục đích
USBInterface cung cấp một phương thức để kết nối và giao tiếp với các thiết bị USB từ trình duyệt web, cho phép người dùng gửi và nhận dữ liệu trực tiếp từ thiết bị mà không cần phần mềm trung gian.

### Cách sử dụng
Để sử dụng USBInterface, bạn cần đảm bảo rằng trình duyệt hỗ trợ API WebUSB. Dưới đây là các bước cơ bản để thiết lập kết nối:

1. **Kết nối với thiết bị USB**: Sử dụng phương thức `navigator.usb.requestDevice()` để yêu cầu người dùng chọn thiết bị USB.
2. **Mở kết nối**: Sau khi thiết bị được chọn, bạn có thể mở kết nối bằng phương thức `device.open()`.
3. **Giao tiếp với thiết bị**: Sử dụng các phương thức như `device.controlTransferOut()` và `device.controlTransferIn()` để gửi và nhận dữ liệu.

### Chi tiết
- **navigator.usb.requestDevice(options)**: Phương thức này hiển thị hộp thoại cho phép người dùng chọn thiết bị USB. Tham số `options` có thể bao gồm `filters` để chỉ định các thiết bị cụ thể.
- **device.open()**: Mở kết nối tới thiết bị đã chọn. Nếu thiết bị đã được mở, phương thức sẽ không thực hiện gì.
- **device.controlTransferOut(request)**: Gửi lệnh đến thiết bị. Tham số `request` là một đối tượng chứa các thông tin như `requestType`, `recipient`, `request`, `value`, và `index`.
- **device.controlTransferIn(request)**: Nhận phản hồi từ thiết bị. Tham số `request` tương tự như `controlTransferOut`.

## Ví dụ
### Kết nối với thiết bị USB
```javascript
async function connectToUSB() {
    try {
        const device = await navigator.usb.requestDevice({ filters: [{ vendorId: 0x1234 }] });
        await device.open();
        console.log('Kết nối thành công với thiết bị:', device);
    } catch (error) {
        console.error('Không thể kết nối:', error);
    }
}
connectToUSB();
```

### Gửi dữ liệu đến thiết bị
```javascript
async function sendData(device, data) {
    try {
        await device.controlTransferOut({
            requestType: 'vendor',
            recipient: 'device',
            request: 0x01,
            value: 0x00,
            index: 0x00
        }, data);
        console.log('Dữ liệu đã được gửi thành công.');
    } catch (error) {
        console.error('Lỗi khi gửi dữ liệu:', error);
    }
}
```

## Giải thích
- **Lỗi thường gặp**: Một số thiết bị USB có thể không hỗ trợ API WebUSB, do đó, việc kiểm tra tính tương thích trước khi cố gắng kết nối là rất quan trọng.
- **Quyền truy cập**: Trình duyệt sẽ yêu cầu người dùng cung cấp quyền truy cập vào thiết bị USB, và nếu không được cấp quyền, bạn sẽ không thể giao tiếp.
- **Hạn chế về bảo mật**: API WebUSB yêu cầu trang web phải được phục vụ qua HTTPS để đảm bảo an toàn khi kết nối với thiết bị.

## Tóm tắt một dòng
USBInterface trong JavaScript cho phép các nhà phát triển kết nối và giao tiếp với các thiết bị USB một cách dễ dàng thông qua API WebUSB.