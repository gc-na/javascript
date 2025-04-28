<!--
Meta Description: # Kết Quả Chuyển Giao USB (USBOutTransferResult) trong JavaScript ## Tóm tắt `USBOutTransferResult` là một đối tượng trong JavaScript được sử dụng để ...
Meta Keywords: giao, chuyển, usb, lệnh, thiết
-->

# Kết Quả Chuyển Giao USB (USBOutTransferResult) trong JavaScript

## Tóm tắt
`USBOutTransferResult` là một đối tượng trong JavaScript được sử dụng để quản lý và nhận biết kết quả của các lệnh chuyển giao dữ liệu từ thiết bị USB ra ngoài. Nó là một phần quan trọng trong API Web USB, giúp các lập trình viên kiểm soát và xử lý các giao tiếp với thiết bị USB.

## Tài liệu
### Mục đích
`USBOutTransferResult` được thiết kế để cung cấp thông tin về kết quả của một lệnh chuyển giao dữ liệu từ máy chủ đến thiết bị USB. Đối tượng này chứa các thuộc tính giúp xác định xem lệnh chuyển giao có thành công hay không, cùng với các chi tiết bổ sung.

### Cách sử dụng
Để sử dụng `USBOutTransferResult`, bạn cần thực hiện một lệnh chuyển giao dữ liệu, thường là thông qua phương thức `transferOut()` của đối tượng `USBDevice`. Sau khi lệnh được thực hiện, một đối tượng `USBOutTransferResult` sẽ được trả về, cho phép bạn kiểm tra trạng thái và kết quả của lệnh chuyển giao.

### Chi tiết
- **Thuộc tính**:
  - `status`: Trạng thái của lệnh chuyển giao (thành công hoặc thất bại).
  - `bytesWritten`: Số byte đã được gửi đi.

- **Phương thức**:
  - `transferOut(endpointNumber, data)`: Gửi dữ liệu tới thiết bị USB.

## Ví dụ
```javascript
async function sendDataToUSBDevice(device, endpoint, data) {
    try {
        const result = await device.transferOut(endpoint, data);
        console.log('Kết quả chuyển giao:', result);
        console.log('Số byte đã gửi:', result.bytesWritten);
    } catch (error) {
        console.error('Lỗi trong quá trình chuyển giao:', error);
    }
}

// Sử dụng hàm
navigator.usb.requestDevice({ filters: [{ vendorId: 0x1234 }] })
    .then(device => {
        return device.open();
    })
    .then(device => {
        return sendDataToUSBDevice(device, 1, new Uint8Array([0x01, 0x02, 0x03]));
    })
    .catch(error => console.error('Lỗi:', error));
```

## Giải thích
Khi làm việc với `USBOutTransferResult`, cần lưu ý một số điểm sau:
- Đảm bảo rằng thiết bị USB đã được kết nối và mở trước khi thực hiện lệnh chuyển giao.
- Kiểm tra kỹ lưỡng các lỗi có thể xảy ra trong quá trình chuyển giao, như thời gian chờ hoặc lỗi thiết bị.
- Số byte thực tế được gửi đi có thể khác với số byte bạn đã cố gắng gửi, vì vậy hãy kiểm tra thuộc tính `bytesWritten`.

## Tóm tắt một dòng
`USBOutTransferResult` là đối tượng JavaScript giúp quản lý và nhận biết kết quả của các lệnh chuyển giao dữ liệu từ thiết bị USB ra ngoài.