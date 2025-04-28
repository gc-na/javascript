<!--
Meta Description: # Cảm biến Gia tốc Tuyến tính (LinearAccelerationSensor) trong JavaScript ## Tóm tắt Cảm biến Gia tốc Tuyến tính (LinearAccelerationSensor) là một API...
Meta Keywords: sensor, cảm, biến, gia, tốc
-->

# Cảm biến Gia tốc Tuyến tính (LinearAccelerationSensor) trong JavaScript

## Tóm tắt
Cảm biến Gia tốc Tuyến tính (LinearAccelerationSensor) là một API trong JavaScript cho phép các nhà phát triển truy cập dữ liệu gia tốc tuyến tính của thiết bị, giúp theo dõi chuyển động mà không bị ảnh hưởng bởi trọng lực.

## Tài liệu
Cảm biến Gia tốc Tuyến tính được sử dụng để đo gia tốc trong ba trục (x, y, z) và cung cấp thông tin về chuyển động của thiết bị. API này rất hữu ích trong việc phát triển các ứng dụng như trò chơi, ứng dụng thể thao, và các ứng dụng theo dõi sức khỏe.

### Cách sử dụng
Để sử dụng Cảm biến Gia tốc Tuyến tính, bạn cần khởi tạo một đối tượng LinearAccelerationSensor và lắng nghe sự kiện `reading` để nhận dữ liệu gia tốc. Dưới đây là cú pháp cơ bản:

```javascript
const sensor = new LinearAccelerationSensor();

sensor.addEventListener('reading', () => {
    console.log(`Gia tốc: X=${sensor.x}, Y=${sensor.y}, Z=${sensor.z}`);
});

// Bắt đầu cảm biến
sensor.start();
```

### Chi tiết
- **Khởi tạo**: Để khởi tạo Cảm biến Gia tốc Tuyến tính, bạn chỉ cần tạo một đối tượng `LinearAccelerationSensor`.
- **Sự kiện**: Sự kiện `reading` sẽ được kích hoạt mỗi khi có dữ liệu mới từ cảm biến.
- **Dừng cảm biến**: Bạn có thể dừng cảm biến bằng cách sử dụng phương thức `stop()`.

## Ví dụ
### Ví dụ đơn giản
```javascript
if ('LinearAccelerationSensor' in window) {
    const sensor = new LinearAccelerationSensor();
    
    sensor.addEventListener('reading', () => {
        console.log(`Gia tốc: X=${sensor.x}, Y=${sensor.y}, Z=${sensor.z}`);
    });

    sensor.start();
} else {
    console.log("Cảm biến Gia tốc Tuyến tính không được hỗ trợ trên thiết bị này.");
}
```

### Ví dụ với xử lý lỗi
```javascript
if ('LinearAccelerationSensor' in window) {
    const sensor = new LinearAccelerationSensor();

    sensor.addEventListener('reading', () => {
        console.log(`Gia tốc: X=${sensor.x}, Y=${sensor.y}, Z=${sensor.z}`);
    });

    sensor.start();
    
    sensor.addEventListener('error', (event) => {
        console.error('Lỗi cảm biến:', event.error.name);
    });
} else {
    console.log("Cảm biến Gia tốc Tuyến tính không được hỗ trợ trên thiết bị này.");
}
```

## Giải thích
Khi sử dụng Cảm biến Gia tốc Tuyến tính, bạn cần chú ý một số vấn đề:
- **Hỗ trợ trình duyệt**: Không phải tất cả các trình duyệt đều hỗ trợ API này. Hãy kiểm tra tính tương thích trước khi triển khai.
- **Quyền truy cập**: Một số thiết bị có thể yêu cầu quyền truy cập vào cảm biến. Đảm bảo rằng ứng dụng của bạn có quyền cần thiết.
- **Lỗi cảm biến**: Xử lý sự kiện `error` là rất quan trọng để đảm bảo rằng người dùng có thể hiểu được vấn đề nếu cảm biến không hoạt động.

## Tóm tắt một dòng
Cảm biến Gia tốc Tuyến tính trong JavaScript cho phép truy cập dữ liệu gia tốc của thiết bị, hỗ trợ phát triển ứng dụng theo dõi chuyển động.