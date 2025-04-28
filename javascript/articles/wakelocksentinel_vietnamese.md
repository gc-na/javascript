<!--
Meta Description: # WakeLockSentinel trong JavaScript: Giữ màn hình luôn sáng ## Tóm tắt `WakeLockSentinel` là một API trong JavaScript cho phép các nhà phát triển giữ ...
Meta Keywords: wake, lock, trong, các, dụng
-->

# WakeLockSentinel trong JavaScript: Giữ màn hình luôn sáng

## Tóm tắt
`WakeLockSentinel` là một API trong JavaScript cho phép các nhà phát triển giữ cho màn hình thiết bị luôn sáng trong quá trình thực hiện các tác vụ quan trọng, như trong các ứng dụng web hoặc game, nhằm cải thiện trải nghiệm người dùng.

## Tài liệu
### Mục đích
`WakeLockSentinel` được sử dụng để ngăn màn hình thiết bị tự động tắt hoặc chuyển sang chế độ ngủ trong khi người dùng đang tương tác với ứng dụng web. Điều này đặc biệt hữu ích cho những ứng dụng cần duy trì sự chú ý của người dùng hoặc cần thực hiện các tác vụ liên tục mà không bị gián đoạn bởi màn hình tắt.

### Cách sử dụng
Để sử dụng `WakeLockSentinel`, bạn cần gọi phương thức `navigator.wakeLock.request()`, và nó sẽ trả về một đối tượng `WakeLockSentinel` nếu thành công. Đối tượng này sẽ duy trì trạng thái "wake lock" cho đến khi bạn gọi phương thức `release()`.

#### Ví dụ cơ bản
```javascript
async function requestWakeLock() {
    try {
        const wakeLock = await navigator.wakeLock.request('screen');
        console.log('Wake Lock is active');

        // Giữ wake lock trong một khoảng thời gian hoặc cho đến khi cần thiết
        // Khi không cần thiết nữa, hãy giải phóng wake lock
        document.addEventListener('visibilitychange', async () => {
            if (document.visibilityState === 'hidden') {
                await wakeLock.release();
                console.log('Wake Lock has been released');
            }
        });
    } catch (err) {
        console.error(`${err.name}, ${err.message}`);
    }
}

requestWakeLock();
```

## Giải thích
### Những cạm bẫy thường gặp
- **Kiểm tra hỗ trợ**: Không phải tất cả các trình duyệt đều hỗ trợ API `Wake Lock`. Trước khi sử dụng, hãy kiểm tra xem trình duyệt có hỗ trợ hay không.
  
- **Giải phóng wake lock**: Đảm bảo rằng bạn gọi phương thức `release()` để giải phóng wake lock khi không còn cần thiết nữa. Nếu không, điều này có thể làm tiêu tốn pin của thiết bị.

- **Chế độ ngủ**: Một số thiết bị có thể không cho phép giữ wake lock khi màn hình tắt hoặc ở chế độ ngủ.

- **Lỗi**: Trong một số trường hợp, việc yêu cầu wake lock có thể bị từ chối, hãy xử lý các lỗi này để nâng cao trải nghiệm người dùng.

## Tóm tắt một dòng
`WakeLockSentinel` trong JavaScript cho phép các ứng dụng web duy trì màn hình sáng để cải thiện trải nghiệm người dùng trong các tác vụ quan trọng.