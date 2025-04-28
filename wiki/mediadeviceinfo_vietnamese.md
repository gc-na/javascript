<!--
Meta Description: # MediaDeviceInfo trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ Sử Dụng ## Tóm tắt MediaDeviceInfo là một giao diện trong JavaScript giúp xác định và ...
Meta Keywords: thiết, dụng, một, các, mediadeviceinfo
-->

# MediaDeviceInfo trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ Sử Dụng

## Tóm tắt
MediaDeviceInfo là một giao diện trong JavaScript giúp xác định và truy cập thông tin về các thiết bị phương tiện, như camera và microphone, được kết nối với máy tính hoặc thiết bị di động. Giao diện này là một phần của WebRTC, cho phép người dùng lựa chọn thiết bị đầu vào cho các ứng dụng web.

## Tài liệu
### Mục đích
MediaDeviceInfo cung cấp thông tin chi tiết về các thiết bị âm thanh và video khả dụng, bao gồm tên thiết bị, loại thiết bị, và ID thiết bị. Điều này hữu ích cho các nhà phát triển khi muốn xây dựng các ứng dụng sử dụng video hoặc âm thanh, như video call hay livestream.

### Cách sử dụng
Để sử dụng MediaDeviceInfo, trước tiên bạn cần truy cập danh sách các thiết bị phương tiện bằng cách sử dụng `navigator.mediaDevices.enumerateDevices()`. Hàm này trả về một Promise chứa danh sách các đối tượng MediaDeviceInfo.

### Chi tiết
- **Thuộc tính**:
  - `deviceId`: Một chuỗi duy nhất xác định thiết bị.
  - `kind`: Loại thiết bị, có thể là `audioinput`, `audiooutput`, hoặc `videoinput`.
  - `label`: Một chuỗi mô tả thiết bị, thường là tên của thiết bị (có thể không khả dụng trên một số trình duyệt vì lý do bảo mật).

### Ví dụ
```javascript
// Lấy danh sách các thiết bị phương tiện
navigator.mediaDevices.enumerateDevices()
  .then(function(devices) {
    devices.forEach(function(device) {
      console.log(device.kind + ": " + device.label + " id = " + device.deviceId);
    });
  })
  .catch(function(err) {
    console.error(err);
  });
```

### Giải thích
- **Điểm cần chú ý**: Một số trình duyệt yêu cầu người dùng cấp quyền truy cập vào thiết bị trước khi có thể lấy thông tin thiết bị. Nếu không có quyền, thuộc tính `label` có thể không được hiển thị.
- **Giới hạn bảo mật**: Để bảo vệ quyền riêng tư của người dùng, một số thuộc tính chỉ có thể được truy cập khi trang web đang sử dụng HTTPS.

## Tóm tắt một dòng
MediaDeviceInfo trong JavaScript cho phép truy cập thông tin chi tiết về các thiết bị âm thanh và video khả dụng trên máy tính hoặc thiết bị di động.