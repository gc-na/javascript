<!--
Meta Description: # Sự kiện onload trong JavaScript: Hướng dẫn Chi tiết và Ví dụ ## Tóm tắt Sự kiện `onload` trong JavaScript là một sự kiện quan trọng cho phép lập trì...
Meta Keywords: onload, được, tài, kiện, tải
-->

# Sự kiện onload trong JavaScript: Hướng dẫn Chi tiết và Ví dụ

## Tóm tắt
Sự kiện `onload` trong JavaScript là một sự kiện quan trọng cho phép lập trình viên thực hiện mã khi một tài liệu hoặc một tài nguyên đã được tải xong. Điều này giúp đảm bảo rằng các phần tử của trang web đã sẵn sàng để tương tác.

## Tài liệu
### Mục đích
Sự kiện `onload` được sử dụng để thực hiện mã JavaScript ngay sau khi tài liệu HTML hoặc các tài nguyên như hình ảnh, script, và stylesheet đã hoàn tất việc tải. Điều này rất hữu ích cho việc khởi tạo các thành phần, thực hiện các thao tác DOM, hoặc bắt đầu các quy trình khác cần có tài nguyên đã sẵn sàng.

### Cách sử dụng
Sự kiện `onload` có thể được áp dụng cho đối tượng `window` hoặc các phần tử cụ thể như hình ảnh. Cú pháp cơ bản là:

```javascript
window.onload = function() {
    // mã JavaScript cần thực thi
};
```

Hoặc cho một phần tử cụ thể:

```javascript
let image = document.getElementById('myImage');
image.onload = function() {
    // mã thực thi sau khi hình ảnh được tải
};
```

### Chi tiết
- **Đối tượng**: `onload` có thể được gán cho đối tượng `window` hoặc các phần tử như `<img>`, `<iframe>`, và `<script>`.
- **Nhiều sự kiện**: Nếu bạn gán nhiều hàm cho `onload`, hàm cuối cùng sẽ được ưu tiên và thực thi.
- **Phương thức addEventListener**: Để thêm nhiều sự kiện mà không ghi đè, bạn nên sử dụng `addEventListener`:

```javascript
window.addEventListener('load', function() {
    // mã thực thi
});
```

## Ví dụ
### Ví dụ 1: Sử dụng cho đối tượng window
```javascript
window.onload = function() {
    console.log('Tài liệu đã được tải xong!');
};
```

### Ví dụ 2: Sử dụng cho hình ảnh
```html
<img id="myImage" src="path/to/image.jpg">

<script>
let image = document.getElementById('myImage');
image.onload = function() {
    console.log('Hình ảnh đã được tải xong!');
};
</script>
```

### Ví dụ 3: Sử dụng addEventListener
```javascript
window.addEventListener('load', function() {
    console.log('Tài liệu và tài nguyên đã được tải xong!');
});
```

## Giải thích
### Những cạm bẫy phổ biến
- **Thứ tự tải**: Nếu bạn cố gắng truy cập các phần tử DOM trước khi chúng được tải, mã của bạn có thể gây lỗi. Luôn đảm bảo rằng mã chạy trong sự kiện `onload` hoặc sau khi trang đã tải xong.
- **Gán nhiều hàm**: Nếu bạn gán nhiều hàm cho `onload`, chỉ hàm cuối cùng sẽ chạy. Sử dụng `addEventListener` để tránh vấn đề này.
- **Sự kiện onload không được gọi trên các tài nguyên đã được cache**: Đôi khi, nếu tài nguyên đã được lưu trong bộ nhớ cache, sự kiện `onload` có thể không được gọi. Để kiểm tra điều này, bạn có thể thử tải lại trang với `Ctrl + F5`.

## Tóm tắt một dòng
Sự kiện `onload` trong JavaScript cho phép thực thi mã khi tài liệu hoặc tài nguyên đã được tải hoàn toàn, đảm bảo rằng các phần tử sẵn sàng để tương tác.