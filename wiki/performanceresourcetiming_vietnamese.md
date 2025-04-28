<!--
Meta Description: # PerformanceResourceTiming trong JavaScript: Tối ưu hóa Hiệu suất Ứng dụng Web ## Tóm tắt `PerformanceResourceTiming` là một API trong JavaScript cho...
Meta Keywords: tài, nguyên, tải, resource, performanceresourcetiming
-->

# PerformanceResourceTiming trong JavaScript: Tối ưu hóa Hiệu suất Ứng dụng Web

## Tóm tắt
`PerformanceResourceTiming` là một API trong JavaScript cho phép lập trình viên theo dõi và phân tích hiệu suất tải tài nguyên trên trang web. Nó cung cấp thông tin chi tiết về thời gian của các giai đoạn khác nhau trong quá trình tải tài nguyên, giúp các nhà phát triển tối ưu hóa trải nghiệm người dùng.

## Tài liệu
### Mục đích
`PerformanceResourceTiming` là một phần của API `Performance` trong JavaScript, được thiết kế để cung cấp thông tin chi tiết về hiệu suất tải tài nguyên như hình ảnh, CSS, JavaScript và các tài nguyên khác. Thông qua các thuộc tính của `PerformanceResourceTiming`, lập trình viên có thể xác định những vấn đề có thể ảnh hưởng đến tốc độ tải trang.

### Sử dụng
Để sử dụng `PerformanceResourceTiming`, bạn có thể truy cập danh sách các tài nguyên đã được tải trên trang thông qua `performance.getEntriesByType('resource')`. Các đối tượng trả về sẽ cung cấp thông tin chi tiết như thời gian bắt đầu tải, thời gian hoàn thành, và nhiều thông số khác.

### Chi tiết
Các thuộc tính chính của `PerformanceResourceTiming` bao gồm:
- `name`: Tên của tài nguyên.
- `entryType`: Loại tài nguyên (thường là "resource").
- `startTime`: Thời điểm bắt đầu tải tài nguyên.
- `duration`: Thời gian hoàn thành tải tài nguyên.
- `transferSize`: Kích thước dữ liệu đã chuyển.
- `responseEnd`: Thời điểm hoàn tất nhận phản hồi từ máy chủ.

## Ví dụ
### Ví dụ cơ bản
```javascript
// Lấy các tài nguyên đã tải
const resources = performance.getEntriesByType('resource');

// Hiển thị thông tin tài nguyên
resources.forEach((resource) => {
    console.log(`Tên tài nguyên: ${resource.name}`);
    console.log(`Thời gian tải: ${resource.duration}ms`);
    console.log(`Kích thước: ${resource.transferSize} bytes`);
});
```

### Ví dụ phân tích thời gian
```javascript
window.onload = () => {
    const resources = performance.getEntriesByType('resource');
    resources.forEach((resource) => {
        if (resource.duration > 1000) { // Tài nguyên nào tải lâu hơn 1 giây
            console.warn(`Tài nguyên ${resource.name} tải lâu: ${resource.duration}ms`);
        }
    });
};
```

## Giải thích
Một số điểm cần lưu ý khi làm việc với `PerformanceResourceTiming`:
- **Bảo mật**: Một số thuộc tính có thể không khả dụng nếu tài nguyên bị tải từ miền khác (CORS).
- **Chỉ số không chính xác**: Thời gian tải có thể bị ảnh hưởng bởi nhiều yếu tố bên ngoài, chẳng hạn như tốc độ mạng hoặc tình trạng máy chủ.
- **Chỉ quan sát tài nguyên**: `PerformanceResourceTiming` chỉ ghi lại thông tin về tài nguyên đã tải, không bao gồm các hoạt động khác trên trang.

## Tóm tắt ngắn gọn
`PerformanceResourceTiming` là một công cụ hữu ích trong JavaScript để theo dõi và tối ưu hóa hiệu suất tải tài nguyên trên trang web.