<!--
Meta Description: # Khả Năng Thiết Bị Nhập (InputDeviceCapabilities) trong JavaScript ## Tóm tắt `InputDeviceCapabilities` là một API trong JavaScript cho phép lập trìn...
Meta Keywords: thiết, inputdevicecapabilities, trợ, năng, kiểm
-->

# Khả Năng Thiết Bị Nhập (InputDeviceCapabilities) trong JavaScript

## Tóm tắt
`InputDeviceCapabilities` là một API trong JavaScript cho phép lập trình viên kiểm tra khả năng của các thiết bị nhập, như chuột và bàn phím, giúp tối ưu hóa trải nghiệm người dùng dựa trên thông tin về thiết bị đang sử dụng.

## Tài liệu
### Mục đích
`InputDeviceCapabilities` được sử dụng để xác định các khả năng cụ thể của thiết bị nhập có sẵn trên trình duyệt. Điều này có thể bao gồm việc kiểm tra xem thiết bị có hỗ trợ các tính năng như cảm ứng hay không, từ đó giúp lập trình viên quyết định cách thức tương tác phù hợp.

### Cách sử dụng
Để sử dụng `InputDeviceCapabilities`, bạn cần tạo một đối tượng mới và truyền vào một `InputDeviceInfo`. Đây là một ví dụ đơn giản:

```javascript
const inputDeviceInfo = new InputDeviceInfo(/* thông tin thiết bị */);
const capabilities = new InputDeviceCapabilities(inputDeviceInfo);
```

### Chi tiết
- **Constructor**: `InputDeviceCapabilities` được khởi tạo với một đối tượng `InputDeviceInfo`. 
- **Thuộc tính**: 
  - `hasTouch`: Kiểm tra xem thiết bị có hỗ trợ cảm ứng hay không.
  - `hasMouse`: Kiểm tra xem thiết bị có hỗ trợ chuột hay không.
  - `hasStylus`: Kiểm tra xem thiết bị có hỗ trợ bút cảm ứng hay không.

## Ví dụ
### Kiểm tra khả năng cảm ứng
```javascript
const inputDeviceInfo = new InputDeviceInfo(/* thông tin thiết bị */);
const capabilities = new InputDeviceCapabilities(inputDeviceInfo);

if (capabilities.hasTouch) {
    console.log("Thiết bị hỗ trợ cảm ứng.");
} else {
    console.log("Thiết bị không hỗ trợ cảm ứng.");
}
```

### Kiểm tra khả năng chuột
```javascript
if (capabilities.hasMouse) {
    console.log("Thiết bị hỗ trợ chuột.");
} else {
    console.log("Thiết bị không hỗ trợ chuột.");
}
```

## Giải thích
- **Cạm bẫy thường gặp**: Một số thiết bị có thể có khả năng hỗ trợ nhưng không được trình duyệt nhận diện chính xác. Điều này có thể xảy ra với các thiết bị không phổ biến hoặc chưa được cập nhật.
- **Ghi chú thêm**: `InputDeviceCapabilities` chủ yếu được sử dụng trong các ứng dụng web phức tạp cần tối ưu hóa trải nghiệm dựa trên thiết bị người dùng.

## Tóm tắt một dòng
`InputDeviceCapabilities` trong JavaScript cho phép lập trình viên kiểm tra khả năng của thiết bị nhập để tối ưu hóa trải nghiệm người dùng.