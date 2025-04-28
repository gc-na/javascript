<!--
Meta Description: # BatteryManager trong JavaScript: Quản lý Năng lượng Thiết bị ## Tóm tắt BatteryManager là một giao diện trong JavaScript cho phép các nhà phát triển...
Meta Keywords: pin, trạng, batterymanager, thái, battery
-->

# BatteryManager trong JavaScript: Quản lý Năng lượng Thiết bị

## Tóm tắt
BatteryManager là một giao diện trong JavaScript cho phép các nhà phát triển truy cập thông tin về trạng thái pin của thiết bị, như mức pin hiện tại, trạng thái sạc, và thời gian còn lại trước khi hết pin.

## Tài liệu
### Mục đích
BatteryManager cung cấp một cách dễ dàng để kiểm tra và theo dõi tình trạng pin của thiết bị. Điều này rất hữu ích cho các ứng dụng web cần tối ưu hóa hiệu suất hoặc điều chỉnh hành vi dựa trên mức năng lượng hiện tại của thiết bị.

### Cách sử dụng
Để sử dụng BatteryManager, bạn có thể truy cập nó thông qua `navigator.getBattery()`, phương thức này trả về một Promise. Khi Promise được giải quyết, nó sẽ trả về một đối tượng BatteryManager.

#### Cú pháp
```javascript
navigator.getBattery().then(function(battery) {
    // Sử dụng đối tượng battery ở đây
});
```

### Chi tiết
Đối tượng BatteryManager có các thuộc tính và phương thức sau:
- **level**: Một giá trị số từ 0 đến 1, đại diện cho mức pin hiện tại (0% - 100%).
- **charging**: Một giá trị boolean cho biết thiết bị có đang sạc hay không.
- **chargingTime**: Thời gian còn lại (tính bằng giây) cho đến khi pin đầy.
- **dischargingTime**: Thời gian còn lại (tính bằng giây) cho đến khi pin hết.

### Sự kiện
BatteryManager cũng hỗ trợ các sự kiện để thông báo cho bạn khi trạng thái pin thay đổi:
- **chargingchange**: Khi trạng thái sạc thay đổi.
- **levelchange**: Khi mức pin thay đổi.

## Ví dụ
### Ví dụ cơ bản
```javascript
navigator.getBattery().then(function(battery) {
    console.log("Mức pin: " + (battery.level * 100) + "%");
    console.log("Đang sạc: " + battery.charging);
    
    battery.addEventListener('chargingchange', function() {
        console.log("Trạng thái sạc đã thay đổi: " + battery.charging);
    });

    battery.addEventListener('levelchange', function() {
        console.log("Mức pin đã thay đổi: " + (battery.level * 100) + "%");
    });
});
```

## Giải thích
### Những điểm cần lưu ý
- Không phải mọi trình duyệt đều hỗ trợ BatteryManager. Kiểm tra tính tương thích trước khi sử dụng.
- Thông tin về trạng thái pin có thể không chính xác nếu thiết bị đang ở chế độ tiết kiệm pin.
- Các sự kiện có thể không được kích hoạt nếu không có sự thay đổi đáng kể trong trạng thái pin.

## Tóm tắt một dòng
BatteryManager trong JavaScript cho phép truy cập và theo dõi thông tin về trạng thái pin của thiết bị, bao gồm mức pin và trạng thái sạc.