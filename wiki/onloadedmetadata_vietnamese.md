<!--
Meta Description: # Sự kiện `loadedmetadata` trong JavaScript: Hướng dẫn chi tiết ## Tóm tắt Sự kiện `loadedmetadata` trong JavaScript được sử dụng để xác định thời điể...
Meta Keywords: video, loadedmetadata, kiện, của, trình
-->

# Sự kiện `loadedmetadata` trong JavaScript: Hướng dẫn chi tiết

## Tóm tắt
Sự kiện `loadedmetadata` trong JavaScript được sử dụng để xác định thời điểm thông tin siêu dữ liệu của một video hoặc âm thanh đã được tải thành công, cho phép lập trình viên thực hiện các thao tác dựa trên thông tin này.

## Tài liệu
Sự kiện `loadedmetadata` được phát sinh trên các phần tử `audio` và `video` khi trình duyệt đã tải xong thông tin siêu dữ liệu của tệp phương tiện. Thông tin này bao gồm độ dài của video hoặc âm thanh, kích thước khung hình, và các thuộc tính khác cần thiết để phát lại.

### Mục đích
Sự kiện này hữu ích cho việc xác định thời gian dài của video/âm thanh, từ đó cho phép lập trình viên có thể điều chỉnh giao diện người dùng hoặc thực hiện các thao tác khác như thiết lập thanh tiến trình.

### Cách sử dụng
Để sử dụng sự kiện `loadedmetadata`, bạn có thể gán một hàm xử lý sự kiện cho phần tử `audio` hoặc `video`. Ví dụ:

```javascript
const videoElement = document.querySelector('video');

videoElement.addEventListener('loadedmetadata', function() {
    console.log('Thời gian dài của video:', videoElement.duration);
});
```

## Ví dụ
Dưới đây là một ví dụ đơn giản về cách sử dụng sự kiện `loadedmetadata`:

```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ví dụ về loadedmetadata</title>
</head>
<body>
    <video controls>
        <source src="video.mp4" type="video/mp4">
        Trình duyệt của bạn không hỗ trợ video.
    </video>
    <script>
        const videoElement = document.querySelector('video');

        videoElement.addEventListener('loadedmetadata', function() {
            console.log('Thời gian dài của video:', videoElement.duration, 'giây');
        });
    </script>
</body>
</html>
```

## Giải thích
Khi làm việc với sự kiện `loadedmetadata`, có một số lưu ý cần chú ý:

- **Thời gian phát**: Đảm bảo rằng bạn chỉ truy cập các thuộc tính như `duration` sau khi sự kiện `loadedmetadata` đã được kích hoạt, để tránh lỗi.
- **Trình duyệt**: Một số trình duyệt có thể có cách xử lý khác nhau về các tệp phương tiện, vì vậy hãy kiểm tra tính tương thích.

## Tóm tắt một dòng
Sự kiện `loadedmetadata` trong JavaScript cho phép lập trình viên biết khi nào siêu dữ liệu của video hoặc âm thanh đã được tải, cung cấp thông tin cần thiết để thực hiện các thao tác tiếp theo.