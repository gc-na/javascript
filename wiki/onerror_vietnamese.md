<!--
Meta Description: # Sự kiện onerror trong JavaScript: Xử lý lỗi hiệu quả ## Tóm tắt Sự kiện `onerror` trong JavaScript cho phép lập trình viên bắt và xử lý các lỗi xảy ...
Meta Keywords: lỗi, onerror, javascript, tải, dụng
-->

# Sự kiện onerror trong JavaScript: Xử lý lỗi hiệu quả

## Tóm tắt
Sự kiện `onerror` trong JavaScript cho phép lập trình viên bắt và xử lý các lỗi xảy ra trong quá trình thực thi mã, đặc biệt là khi tải tài nguyên như hình ảnh hoặc tập tin JavaScript.

## Tài liệu
Sự kiện `onerror` là một thuộc tính của các đối tượng như `window`, `HTMLImageElement`, và `ScriptElement`. Khi một lỗi xảy ra trong quá trình tải tài nguyên, sự kiện này sẽ được kích hoạt, cho phép lập trình viên thực hiện các hành động xử lý lỗi.

### Mục đích
- Bắt lỗi xảy ra trong quá trình tải tài nguyên.
- Cung cấp thông tin chi tiết về lỗi để xử lý một cách thích hợp.

### Cách sử dụng
Sự kiện `onerror` có thể được sử dụng như sau:

```javascript
window.onerror = function(message, source, lineno, colno, error) {
    console.error("Lỗi xảy ra:", message);
    // Thêm mã xử lý lỗi tại đây
};
```

Đối với hình ảnh, bạn có thể sử dụng:

```javascript
const img = new Image();
img.onerror = function() {
    console.log("Không thể tải hình ảnh.");
};
img.src = 'path/to/image.jpg';
```

## Ví dụ
### Ví dụ 1: Bắt lỗi toàn cục
```javascript
window.onerror = function(message, source, lineno, colno, error) {
    alert(`Lỗi: ${message} tại ${source}:${lineno}:${colno}`);
};
```

### Ví dụ 2: Bắt lỗi tải hình ảnh
```javascript
const img = new Image();
img.onerror = function() {
    console.log("Hình ảnh không thể tải.");
};
img.src = 'invalid-path.jpg';
```

## Giải thích
- **Một số cạm bẫy**: Khi sử dụng `onerror`, bạn cần lưu ý rằng nó chỉ bắt lỗi xảy ra trong cùng một miền (same-origin policy). Nếu tài nguyên được tải từ một miền khác và không cung cấp thông tin CORS thích hợp, sự kiện có thể không hoạt động như mong đợi.
  
- **Báo cáo lỗi**: Sử dụng `onerror` có thể giúp bạn báo cáo lỗi cho các dịch vụ theo dõi lỗi, giúp cải thiện chất lượng ứng dụng.

- **Những điều cần tránh**: Tránh việc sử dụng `onerror` cho các lỗi không nghiêm trọng, vì nó có thể làm cho mã trở nên khó đọc và bảo trì.

## Tóm tắt một dòng
Sự kiện `onerror` trong JavaScript giúp lập trình viên bắt và xử lý các lỗi xảy ra khi tải tài nguyên, cải thiện khả năng xử lý lỗi của ứng dụng.