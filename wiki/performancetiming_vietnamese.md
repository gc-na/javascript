<!--
Meta Description: # Hiệu Suất Thời Gian (PerformanceTiming) trong JavaScript ## Tóm Tắt `PerformanceTiming` là một giao diện trong JavaScript cung cấp thông tin chi tiế...
Meta Keywords: thời, timing, tải, gian, trang
-->

# Hiệu Suất Thời Gian (PerformanceTiming) trong JavaScript

## Tóm Tắt
`PerformanceTiming` là một giao diện trong JavaScript cung cấp thông tin chi tiết về thời gian tải và hiệu suất của một trang web, giúp các nhà phát triển tối ưu hóa trải nghiệm người dùng.

## Tài Liệu
`PerformanceTiming` là một phần của API Performance, cho phép các lập trình viên truy cập thông tin về các sự kiện quan trọng trong quá trình tải trang. Nó bao gồm nhiều thuộc tính mô tả thời gian từ khi bắt đầu tải trang đến khi hoàn tất, cũng như các thời điểm quan trọng khác trong chu kỳ tải.

### Mục Đích
Mục đích chính của `PerformanceTiming` là giúp các nhà phát triển hiểu rõ hơn về các yếu tố ảnh hưởng đến hiệu suất tải trang, từ đó có thể cải thiện tốc độ và trải nghiệm người dùng.

### Cách Sử Dụng
Để sử dụng `PerformanceTiming`, bạn có thể truy cập đối tượng `performance.timing` trong JavaScript. Dưới đây là một số thuộc tính chính mà bạn có thể sử dụng:

- `navigationStart`: Thời điểm bắt đầu điều hướng.
- `unloadEventStart`: Thời điểm bắt đầu sự kiện unload.
- `unloadEventEnd`: Thời điểm kết thúc sự kiện unload.
- `connectStart`: Thời điểm bắt đầu kết nối đến máy chủ.
- `responseEnd`: Thời điểm nhận được phản hồi từ máy chủ.
- `domComplete`: Thời điểm DOM hoàn tất.

Ví dụ về cách lấy thông tin từ `PerformanceTiming`:

```javascript
window.onload = function() {
    var timing = performance.timing;
    console.log("Thời gian tải trang: " + (timing.loadEventEnd - timing.navigationStart) + " ms");
};
```

## Ví Dụ
### Ví Dụ Cơ Bản
Dưới đây là một ví dụ đơn giản để hiển thị thời gian tải trang:

```javascript
window.onload = function() {
    var timing = performance.timing;
    var loadTime = timing.loadEventEnd - timing.navigationStart;
    console.log("Thời gian tải trang: " + loadTime + " ms");
};
```

### Ví Dụ Nâng Cao
Bạn có thể sử dụng các thuộc tính khác nhau để phân tích hiệu suất:

```javascript
window.onload = function() {
    var timing = performance.timing;
    var connectTime = timing.connectEnd - timing.connectStart;
    var domReadyTime = timing.domContentLoadedEventEnd - timing.navigationStart;
    
    console.log("Thời gian kết nối: " + connectTime + " ms");
    console.log("Thời gian DOM sẵn sàng: " + domReadyTime + " ms");
};
```

## Giải Thích
Một số lưu ý khi sử dụng `PerformanceTiming`:

- **Chỉ Số Không Chính Xác**: Thời gian có thể không chính xác trong một số trường hợp do các yếu tố bên ngoài như tốc độ mạng.
- **Chỉ Có Sẵn Sau Khi Tải Xong**: Đối tượng `performance.timing` chỉ có thể được truy cập sau khi trang đã tải xong, vì vậy hãy chắc chắn rằng bạn sử dụng nó trong sự kiện `load`.
- **Không Ghi Lại Nhiều Lần**: Những thông tin này sẽ không được ghi lại nếu trang được tải lại, vì vậy bạn cần lưu ý về việc lưu trữ dữ liệu nếu cần thiết.

## Tóm Tắt Một Dòng
`PerformanceTiming` trong JavaScript cung cấp thông tin chi tiết về thời gian tải trang, giúp tối ưu hóa hiệu suất và trải nghiệm người dùng.