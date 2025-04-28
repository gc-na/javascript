<!--
Meta Description: # Cảm Biến Trọng Lực (GravitySensor) trong JavaScript ## Tóm Tắt Cảm biến trọng lực (GravitySensor) là một API trong JavaScript cho phép các nhà phát ...
Meta Keywords: sensor, cảm, biến, gravitysensor, dụng
-->

# Cảm Biến Trọng Lực (GravitySensor) trong JavaScript

## Tóm Tắt
Cảm biến trọng lực (GravitySensor) là một API trong JavaScript cho phép các nhà phát triển truy cập thông tin về trọng lực, giúp tạo ra các ứng dụng tương tác và thú vị thông qua việc theo dõi chuyển động của thiết bị.

## Tài Liệu
### Mục Đích
Cảm biến trọng lực cung cấp thông tin về gia tốc của thiết bị trong không gian ba chiều, liên quan đến trọng lực. Điều này có thể được sử dụng để phát triển các ứng dụng di động hoặc web mà yêu cầu hiểu biết về vị trí và chuyển động của thiết bị.

### Cách Sử Dụng
Để sử dụng GravitySensor, bạn cần tạo một thể hiện của đối tượng GravitySensor và lắng nghe các sự kiện để nhận thông tin về gia tốc. Dưới đây là cú pháp cơ bản:

```javascript
const sensor = new GravitySensor();

sensor.start();

sensor.addEventListener('reading', () => {
    console.log(`Gia tốc X: ${sensor.x}`);
    console.log(`Gia tốc Y: ${sensor.y}`);
    console.log(`Gia tốc Z: ${sensor.z}`);
});

sensor.addEventListener('error', (event) => {
    console.error('Lỗi cảm biến:', event.error);
});
```

### Chi Tiết
- **Khởi Tạo**: Một đối tượng GravitySensor có thể được khởi tạo bằng cách sử dụng từ khóa `new`. 
- **Bắt Đầu**: Phương thức `start()` được gọi để bắt đầu theo dõi dữ liệu cảm biến.
- **Sự Kiện**: Sự kiện `reading` sẽ được phát ra mỗi khi có dữ liệu mới từ cảm biến. Bạn có thể lấy giá trị gia tốc theo trục X, Y, Z thông qua các thuộc tính `x`, `y`, và `z`.
- **Xử Lý Lỗi**: Sự kiện `error` sẽ được phát ra nếu có vấn đề xảy ra trong quá trình truy cập cảm biến.

## Ví Dụ
### Ví Dụ Cơ Bản
```javascript
if ('GravitySensor' in window) {
    const sensor = new GravitySensor();
    
    sensor.start();
    
    sensor.addEventListener('reading', () => {
        console.log(`Gia tốc X: ${sensor.x}`);
        console.log(`Gia tốc Y: ${sensor.y}`);
        console.log(`Gia tốc Z: ${sensor.z}`);
    });

    sensor.addEventListener('error', (event) => {
        console.error('Lỗi cảm biến:', event.error);
    });
} else {
    console.warn('Cảm biến trọng lực không được hỗ trợ trên thiết bị này.');
}
```

## Giải Thích
- **Hỗ Trợ Thiết Bị**: Không phải tất cả các thiết bị đều hỗ trợ GravitySensor. Bạn nên kiểm tra sự hỗ trợ trước khi sử dụng.
- **Quyền Truy Cập**: Một số trình duyệt yêu cầu cấp quyền truy cập để sử dụng cảm biến, vì vậy hãy đảm bảo rằng ứng dụng của bạn xử lý điều này.
- **Tần Suất Đọc**: Tần suất đọc dữ liệu từ cảm biến có thể thay đổi tùy theo thiết bị và môi trường, điều này có thể ảnh hưởng đến độ chính xác của dữ liệu.

## Tóm Tắt Một Dòng
Cảm biến trọng lực (GravitySensor) trong JavaScript cho phép truy cập thông tin gia tốc của thiết bị, hỗ trợ phát triển ứng dụng tương tác.