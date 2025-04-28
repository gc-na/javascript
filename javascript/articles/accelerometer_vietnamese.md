<!--
Meta Description: # Cảm Biến Gia Tốc (Accelerometer) Trong JavaScript ## Tóm Tắt Cảm biến gia tốc trong JavaScript là một phần của API Sensor, cho phép các nhà phát tri...
Meta Keywords: accelerometer, cảm, biến, gia, tốc
-->

# Cảm Biến Gia Tốc (Accelerometer) Trong JavaScript 

## Tóm Tắt
Cảm biến gia tốc trong JavaScript là một phần của API Sensor, cho phép các nhà phát triển truy cập thông tin về gia tốc của thiết bị di động, giúp cải thiện trải nghiệm người dùng trong các ứng dụng web.

## Tài Liệu
### Mục Đích
Cảm biến gia tốc (Accelerometer) cho phép ứng dụng web nhận diện cách thiết bị di động hoặc máy tính bảng di chuyển trong không gian ba chiều, từ đó tạo ra các phản hồi tương tác mượt mà hơn.

### Cách Sử Dụng
Để sử dụng cảm biến gia tốc trong JavaScript, bạn cần sử dụng API `Accelerometer`. Dưới đây là cách khởi tạo và lắng nghe các thay đổi về gia tốc:

1. **Khởi Tạo Cảm Biến Gia Tốc**
```javascript
if ('Accelerometer' in window) {
    const accelerometer = new Accelerometer({ frequency: 60 });
    accelerometer.start();
}
```

2. **Lắng Nghe Dữ Liệu Gia Tốc**
```javascript
accelerometer.addEventListener('reading', () => {
    console.log(`X: ${accelerometer.x}, Y: ${accelerometer.y}, Z: ${accelerometer.z}`);
});
```

### Chi Tiết
- **Cấu Hình**: Bạn có thể tùy chỉnh tần suất (frequency) mà cảm biến gửi dữ liệu. Mặc định tần suất là 60Hz.
- **Quyền Truy Cập**: Trước khi sử dụng, bạn cần đảm bảo rằng người dùng đã cấp quyền cho ứng dụng để truy cập cảm biến.
- **Tương Thích**: Kiểm tra tính tương thích của API với các trình duyệt hiện tại.

## Ví Dụ
### Ví Dụ Cơ Bản
```javascript
if ('Accelerometer' in window) {
    const accelerometer = new Accelerometer({ frequency: 30 });
    accelerometer.addEventListener('reading', () => {
        console.log(`X: ${accelerometer.x}, Y: ${accelerometer.y}, Z: ${accelerometer.z}`);
    });
    accelerometer.start();
} else {
    console.error("Accelerometer is not supported on this device.");
}
```

## Giải Thích
- **Lỗi Thường Gặp**: Một số trình duyệt có thể không hỗ trợ API này, do đó bạn nên kiểm tra tính tương thích trước khi sử dụng.
- **Quyền Truy Cập**: Nếu quyền truy cập bị từ chối, cảm biến sẽ không hoạt động. Hãy xử lý các lỗi này bằng cách thông báo cho người dùng.
- **Chạy Trong HTTPS**: API cảm biến yêu cầu trang web phải chạy trên HTTPS để bảo mật.

## Tóm Tắt Một Dòng
Cảm biến gia tốc trong JavaScript cho phép truy cập dữ liệu gia tốc của thiết bị, hỗ trợ các ứng dụng web tương tác hơn.