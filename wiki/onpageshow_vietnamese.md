<!--
Meta Description: # Sự kiện onpageshow trong JavaScript: Hướng dẫn Chi tiết ## Tóm tắt Sự kiện `onpageshow` trong JavaScript được sử dụng để xử lý các tình huống khi mộ...
Meta Keywords: được, trang, kiện, onpageshow, event
-->

# Sự kiện onpageshow trong JavaScript: Hướng dẫn Chi tiết

## Tóm tắt
Sự kiện `onpageshow` trong JavaScript được sử dụng để xử lý các tình huống khi một trang web được hiển thị, bao gồm việc tải lại trang và điều hướng tới trang từ bộ nhớ cache. Sự kiện này rất hữu ích trong việc quản lý trạng thái và tương tác của người dùng trên các trang web.

## Tài liệu
### Mục đích
Sự kiện `onpageshow` được kích hoạt khi một trang web được hiển thị lại, cho phép nhà phát triển thực hiện các hành động cụ thể, như khôi phục trạng thái trước đó hoặc tải dữ liệu cần thiết từ máy chủ.

### Cách sử dụng
Sự kiện này có thể được gán cho đối tượng `window` hoặc `document`. Cú pháp cơ bản như sau:

```javascript
window.onpageshow = function(event) {
    // Xử lý sự kiện ở đây
};
```

Hoặc sử dụng phương pháp `addEventListener`:

```javascript
window.addEventListener('pageshow', function(event) {
    // Xử lý sự kiện ở đây
});
```

### Tham số
- `event`: Đối tượng sự kiện chứa thông tin về sự kiện `onpageshow`, bao gồm thuộc tính `persisted` cho biết liệu trang có được hiển thị từ bộ nhớ cache hay không.

## Ví dụ
### Ví dụ cơ bản về onpageshow
```javascript
window.addEventListener('pageshow', function(event) {
    if (event.persisted) {
        console.log("Trang được hiển thị từ bộ nhớ cache.");
    } else {
        console.log("Trang được tải mới.");
    }
});
```

### Ví dụ khôi phục trạng thái
```javascript
let previousState = {};

window.addEventListener('pageshow', function(event) {
    if (event.persisted) {
        // Khôi phục trạng thái trước đó
        restoreState(previousState);
    } else {
        // Lưu trạng thái hiện tại
        previousState = saveCurrentState();
    }
});
```

## Giải thích
### Các vấn đề thường gặp
- **Không kích hoạt sự kiện khi không có điều hướng**: Sự kiện `onpageshow` không được kích hoạt nếu trang không được tải lại hoặc điều hướng từ một trang khác.
- **Khác biệt giữa onpageshow và onload**: `onpageshow` có thể được kích hoạt nhiều lần khi điều hướng giữa các trang khác nhau, trong khi `onload` chỉ được gọi một lần khi trang được tải.

### Lưu ý bổ sung
- Sử dụng thuộc tính `event.persisted` để kiểm tra xem trang có được tải từ bộ nhớ cache hay không có thể giúp tối ưu hóa hiệu suất và trải nghiệm người dùng.
- Sự kiện này rất hữu ích cho các ứng dụng web đơn trang (SPA) nơi trạng thái người dùng cần được duy trì.

## Tóm tắt một câu
Sự kiện `onpageshow` trong JavaScript cho phép xử lý các tình huống khi một trang được hiển thị lại, hỗ trợ khôi phục trạng thái và điều chỉnh trải nghiệm người dùng.