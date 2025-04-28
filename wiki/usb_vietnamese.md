<!--
Meta Description: # USB trong JavaScript: Hướng dẫn chi tiết và tối ưu SEO ## Tóm tắt USB (Universal Serial Bus) là một giao thức kết nối phổ biến, cho phép JavaScript ...
Meta Keywords: thiết, usb, kết, nối, với
-->

# USB trong JavaScript: Hướng dẫn chi tiết và tối ưu SEO

## Tóm tắt
USB (Universal Serial Bus) là một giao thức kết nối phổ biến, cho phép JavaScript tương tác với thiết bị USB thông qua WebUSB API, giúp phát triển ứng dụng web có khả năng giao tiếp trực tiếp với phần cứng.

## Tài liệu
### Mục đích
WebUSB API mang đến khả năng giao tiếp giữa trình duyệt và thiết bị USB. Điều này cho phép các lập trình viên JavaScript phát triển ứng dụng web có thể kết nối và tương tác với các thiết bị như máy in, cảm biến, và nhiều thiết bị khác.

### Cách sử dụng
Để sử dụng WebUSB trong JavaScript, bạn cần phải thực hiện các bước sau:
1. **Kết nối với thiết bị USB**: Sử dụng `navigator.usb.requestDevice()` để yêu cầu người dùng chọn thiết bị USB.
2. **Kết nối và giao tiếp**: Sau khi thiết bị được chọn, bạn có thể kết nối và gửi/nhận dữ liệu thông qua các phương thức của đối tượng thiết bị.

### Chi tiết
WebUSB API có các phương thức và thuộc tính chính sau:
- **requestDevice(options)**: Yêu cầu thiết bị USB từ người dùng.
- **open()**: Mở kết nối với thiết bị đã chọn.
- **selectConfiguration(configurationValue)**: Chọn cấu hình cho thiết bị USB.
- **claimInterface(interfaceNumber)**: Chiếm quyền điều khiển một giao diện của thiết bị.
- **transferIn(endpointNumber, length)**: Nhận dữ liệu từ thiết bị.
- **transferOut(endpointNumber, data)**: Gửi dữ liệu đến thiết bị.

## Ví dụ
Dưới đây là một ví dụ đơn giản về cách sử dụng WebUSB để kết nối với thiết bị USB:

```javascript
async function connectToUSB() {
    try {
        const device = await navigator.usb.requestDevice({ filters: [{ vendorId: 0x1234 }] });
        await device.open(); // Mở kết nối
        await device.selectConfiguration(1); // Chọn cấu hình
        await device.claimInterface(0); // Chiếm giao diện

        const data = new Uint8Array([0x01, 0x02, 0x03]);
        await device.transferOut(1, data); // Gửi dữ liệu
        const receivedData = await device.transferIn(1, 64); // Nhận dữ liệu
        console.log(receivedData.data); // Hiển thị dữ liệu nhận được
    } catch (error) {
        console.error("Có lỗi xảy ra:", error);
    }
}
```

## Giải thích
### Những điều cần chú ý
- **Quyền truy cập**: Người dùng phải cấp quyền cho trình duyệt để kết nối với thiết bị USB.
- **Hỗ trợ trình duyệt**: WebUSB không được hỗ trợ trên tất cả các trình duyệt. Hiện tại, nó chủ yếu được hỗ trợ trên Chrome và các trình duyệt dựa trên Chromium.
- **Cấu hình thiết bị**: Đảm bảo rằng bạn đã chọn đúng cấu hình và giao diện của thiết bị trước khi thực hiện các thao tác gửi/nhận dữ liệu.

## Tóm tắt một dòng
WebUSB cho phép JavaScript giao tiếp trực tiếp với thiết bị USB, mở ra khả năng phát triển ứng dụng web tương tác với phần cứng.