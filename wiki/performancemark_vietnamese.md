<!--
Meta Description: # Hiệu Suất Mark trong JavaScript: Tối Ưu Hóa Hiệu Suất Ứng Dụng ## Tóm Tắt PerformanceMark là một API trong JavaScript cho phép lập trình viên ghi lạ...
Meta Keywords: dụng, đánh, dấu, các, hiệu
-->

# Hiệu Suất Mark trong JavaScript: Tối Ưu Hóa Hiệu Suất Ứng Dụng

## Tóm Tắt
PerformanceMark là một API trong JavaScript cho phép lập trình viên ghi lại các điểm đánh dấu hiệu suất trong ứng dụng web, giúp theo dõi và cải thiện hiệu suất của ứng dụng.

## Tài Liệu
### Mục Đích
PerformanceMark được sử dụng để tạo các điểm đánh dấu trong quá trình thực thi của ứng dụng. Điều này cho phép lập trình viên xác định thời gian cần thiết để thực hiện một số tác vụ nhất định, từ đó tối ưu hóa hiệu suất của ứng dụng.

### Cách Sử Dụng
Để sử dụng PerformanceMark, bạn có thể gọi phương thức `performance.mark()` với một tên đánh dấu mà bạn mong muốn. Các điểm đánh dấu này có thể được truy xuất sau đó bằng cách sử dụng `performance.getEntriesByType("mark")`.

#### Cú Pháp
```javascript
performance.mark('tênĐánhDấu');
```

### Ví Dụ
#### Ví Dụ Cơ Bản
```javascript
// Ghi lại thời điểm bắt đầu
performance.mark('start');

// Một số tác vụ cần thực hiện
for (let i = 0; i < 1000000; i++) {
    // Thực hiện công việc gì đó
}

// Ghi lại thời điểm kết thúc
performance.mark('end');

// Lấy thông tin các điểm đánh dấu
performance.measure('tổngThờiGian', 'start', 'end');

// Hiển thị kết quả
console.log(performance.getEntriesByType('measure'));
```

## Giải Thích
### Những Lưu Ý Chung
- **Đánh dấu Nhiều Lần**: Bạn có thể tạo nhiều đánh dấu với tên khác nhau để theo dõi nhiều phần của ứng dụng.
- **Tính Chính Xác**: Đảm bảo rằng các điểm đánh dấu được ghi lại ở những vị trí chính xác để có thể đo lường hiệu suất một cách chính xác.
- **Trình Duyệt Hỗ Trợ**: Kiểm tra tính tương thích của API này với các trình duyệt mà ứng dụng của bạn sẽ hoạt động.

### Cạm Bẫy Thường Gặp
- **Tên Đánh Dấu Trùng Lặp**: Nếu bạn sử dụng cùng một tên đánh dấu nhiều lần, nó có thể gây nhầm lẫn trong việc phân tích dữ liệu hiệu suất.
- **Thời Gian Phân Tích**: Đảm bảo rằng các tác vụ thực hiện giữa các điểm đánh dấu không bị ảnh hưởng bởi các yếu tố bên ngoài, chẳng hạn như mạng hoặc tài nguyên khác.

## Tóm Tắt Một Dòng
PerformanceMark trong JavaScript cho phép lập trình viên ghi lại các điểm đánh dấu hiệu suất, giúp cải thiện hiệu suất của ứng dụng web.