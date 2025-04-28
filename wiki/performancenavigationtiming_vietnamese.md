<!--
Meta Description: # Hiểu về PerformanceNavigationTiming trong JavaScript: Tối ưu hóa hiệu suất trang web ## Tóm tắt PerformanceNavigationTiming là một giao diện trong J...
Meta Keywords: tải, các, liệu, performancenavigationtiming, trang
-->

# Hiểu về PerformanceNavigationTiming trong JavaScript: Tối ưu hóa hiệu suất trang web

## Tóm tắt
PerformanceNavigationTiming là một giao diện trong JavaScript cung cấp thông tin chi tiết về quá trình điều hướng của một tài liệu. Nó giúp các nhà phát triển theo dõi và phân tích hiệu suất tải trang, từ đó tối ưu hóa trải nghiệm người dùng.

## Tài liệu
PerformanceNavigationTiming là một phần trong API Performance của trình duyệt, cho phép truy cập các thông tin liên quan đến việc điều hướng trang. Giao diện này mở rộng PerformanceTiming, cung cấp thêm dữ liệu về các sự kiện điều hướng.

### Mục đích
Mục đích chính của PerformanceNavigationTiming là cung cấp các chỉ số hữu ích về hiệu suất tải trang, giúp nhà phát triển hiểu rõ hơn về thời gian cần thiết để tải một tài liệu, từ đó tối ưu hóa trải nghiệm người dùng.

### Cách sử dụng
Để sử dụng PerformanceNavigationTiming, bạn có thể truy cập đối tượng `performance` trong JavaScript, sau đó gọi `getEntriesByType('navigation')` để lấy các thông tin liên quan.

```javascript
const navigationEntries = performance.getEntriesByType('navigation');
console.log(navigationEntries);
```

### Chi tiết
PerformanceNavigationTiming cung cấp các thuộc tính như:
- `startTime`: Thời gian bắt đầu tải tài liệu.
- `duration`: Tổng thời gian tải tài liệu.
- `transferSize`: Kích thước tổng thể của tài liệu được tải.

Các thuộc tính này giúp phân tích hiệu suất tải trang và xác định các điểm nghẽn có thể xảy ra.

## Ví dụ
### Ví dụ 1: Lấy thông tin điều hướng
```javascript
window.onload = () => {
    const navigationEntries = performance.getEntriesByType('navigation');
    if (navigationEntries.length > 0) {
        const navTiming = navigationEntries[0];
        console.log(`Thời gian tải: ${navTiming.duration}ms`);
    }
};
```

### Ví dụ 2: Phân tích thời gian tải
```javascript
const navTiming = performance.getEntriesByType('navigation')[0];
console.log(`Thời gian bắt đầu: ${navTiming.startTime}ms`);
console.log(`Kích thước tải: ${navTiming.transferSize} bytes`);
```

## Giải thích
Khi làm việc với PerformanceNavigationTiming, có một số điều cần lưu ý:
- Không phải mọi trình duyệt đều hỗ trợ API này. Hãy kiểm tra tính tương thích trước khi sử dụng.
- Dữ liệu chỉ có sẵn sau khi tài liệu đã tải xong, vì vậy hãy đảm bảo thực hiện các lệnh trong sự kiện `load`.
- Các chỉ số có thể thay đổi dựa trên cách người dùng truy cập trang (ví dụ: từ bookmark, liên kết bên ngoài, hoặc điều hướng từ trang khác).

## Tóm tắt một dòng
PerformanceNavigationTiming trong JavaScript cung cấp thông tin về hiệu suất điều hướng của trang web, giúp tối ưu hóa trải nghiệm người dùng.