<!--
Meta Description: # WakeLock trong JavaScript: Giữ Màn Hình Luôn Bật ## Tóm tắt WakeLock là một API trong JavaScript cho phép các nhà phát triển giữ cho màn hình thiết ...
Meta Keywords: wakelock, wake, lock, thiết, console
-->

# WakeLock trong JavaScript: Giữ Màn Hình Luôn Bật

## Tóm tắt
WakeLock là một API trong JavaScript cho phép các nhà phát triển giữ cho màn hình thiết bị luôn bật khi ứng dụng của họ đang chạy. Điều này rất hữu ích cho các ứng dụng cần duy trì sự chú ý của người dùng, như các ứng dụng video hay trò chơi.

## Tài liệu
### Mục đích
WakeLock được thiết kế để ngăn màn hình thiết bị tự động tắt. Điều này giúp cải thiện trải nghiệm người dùng, đặc biệt trong các tình huống mà việc hiển thị thông tin liên tục là cần thiết.

### Cách sử dụng
Để sử dụng WakeLock, bạn cần truy cập vào API thông qua đối tượng `navigator`. Có hai loại WakeLock:
1. **Screen Wake Lock**: Giữ cho màn hình luôn sáng.
2. **System Wake Lock**: Giữ cho hệ thống không vào chế độ ngủ.

### Cú pháp cơ bản
```javascript
// Kiểm tra hỗ trợ Wake Lock
if ('wakeLock' in navigator) {
    // Đặt Wake Lock
    async function requestWakeLock() {
        try {
            const wakeLock = await navigator.wakeLock.request('screen');
            console.log('Wake Lock đã được kích hoạt');

            // Giải phóng Wake Lock khi không còn cần thiết
            document.addEventListener('visibilitychange', async () => {
                if (document.visibilityState === 'hidden') {
                    await wakeLock.release();
                    console.log('Wake Lock đã được giải phóng');
                }
            });
        } catch (err) {
            console.error(`${err.name}, ${err.message}`);
        }
    }
    requestWakeLock();
} else {
    console.log('Trình duyệt không hỗ trợ Wake Lock API');
}
```

## Ví dụ
### Ví dụ cơ bản về WakeLock
```javascript
async function activateWakeLock() {
    if ('wakeLock' in navigator) {
        try {
            const wakeLock = await navigator.wakeLock.request('screen');
            console.log('Wake Lock đã được kích hoạt');

            // Giải phóng Wake Lock khi không còn cần thiết
            document.addEventListener('visibilitychange', async () => {
                if (document.visibilityState === 'hidden') {
                    await wakeLock.release();
                    console.log('Wake Lock đã được giải phóng');
                }
            });
        } catch (error) {
            console.error(`Lỗi: ${error.name}, ${error.message}`);
        }
    } else {
        console.log('Trình duyệt của bạn không hỗ trợ Wake Lock API');
    }
}

activateWakeLock();
```

## Giải thích
### Những cạm bẫy thường gặp
- **Hỗ trợ trình duyệt**: Không phải tất cả các trình duyệt đều hỗ trợ WakeLock API. Đảm bảo kiểm tra hỗ trợ trước khi sử dụng.
- **Giải phóng Wake Lock**: Luôn nhớ giải phóng Wake Lock khi không còn cần thiết, để tránh làm tiêu tốn pin của thiết bị.
- **Tương tác với người dùng**: Một số trình duyệt yêu cầu tương tác từ người dùng (như nhấp chuột) để kích hoạt Wake Lock.

## Tóm tắt một dòng
WakeLock trong JavaScript là một API cho phép giữ màn hình thiết bị luôn bật, cải thiện trải nghiệm người dùng cho các ứng dụng cần hiển thị liên tục.