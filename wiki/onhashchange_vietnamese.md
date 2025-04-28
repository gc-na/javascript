<!--
Meta Description: # Sự kiện onhashchange trong JavaScript: Cách sử dụng và ví dụ ## Tóm tắt Sự kiện `onhashchange` trong JavaScript cho phép bạn theo dõi và xử lý thay ...
Meta Keywords: hash, onhashchange, trong, kiện, dụng
-->

# Sự kiện onhashchange trong JavaScript: Cách sử dụng và ví dụ

## Tóm tắt
Sự kiện `onhashchange` trong JavaScript cho phép bạn theo dõi và xử lý thay đổi trong phần hash của URL, giúp quản lý điều hướng trong các ứng dụng web mà không cần tải lại trang.

## Tài liệu
### Mục đích
Sự kiện `onhashchange` được kích hoạt khi phần hash (phần sau dấu #) của URL thay đổi. Điều này rất hữu ích trong các ứng dụng một trang (SPA) nơi bạn cần cập nhật nội dung mà không làm mới toàn bộ trang.

### Cách sử dụng
Để sử dụng `onhashchange`, bạn chỉ cần gán một hàm xử lý sự kiện cho thuộc tính này của đối tượng `window`. Dưới đây là cú pháp cơ bản:

```javascript
window.onhashchange = function() {
    // Xử lý khi hash thay đổi
};
```

### Chi tiết
Sự kiện này được hỗ trợ trên hầu hết các trình duyệt hiện đại. Tuy nhiên, nó không làm việc với các thay đổi của URL khi hash không thay đổi. Để nhận diện hash, bạn có thể sử dụng `location.hash` để lấy giá trị hiện tại.

## Ví dụ
### Ví dụ cơ bản
Dưới đây là một ví dụ đơn giản về cách sử dụng `onhashchange`:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Ví dụ onhashchange</title>
</head>
<body>
    <h1>Demo onhashchange</h1>
    <a href="#home">Trang chủ</a>
    <a href="#about">Giới thiệu</a>
    <a href="#contact">Liên hệ</a>
    
    <div id="content"></div>

    <script>
        window.onhashchange = function() {
            const hash = location.hash.substring(1); // Lấy giá trị hash
            document.getElementById('content').innerText = "Bạn đang ở: " + hash;
        };

        // Sự kiện khởi tạo
        window.onhashchange();
    </script>
</body>
</html>
```

### Kết quả
Khi người dùng nhấp vào các liên kết, nội dung trong `div` sẽ cập nhật để hiển thị phần hash hiện tại trong URL.

## Giải thích
### Những điều cần lưu ý
- Sự kiện `onhashchange` không được kích hoạt khi thay đổi hash bằng JavaScript mà không có sự tương tác của người dùng.
- Nếu bạn cần thực hiện hành động khi hash thay đổi mà không chỉ định lại hàm, hãy sử dụng `addEventListener`:

```javascript
window.addEventListener('hashchange', function() {
    // Xử lý tại đây
});
```

- Hãy đảm bảo rằng bạn đã xem xét các trình duyệt cũ, vì một số trình duyệt có thể không hỗ trợ sự kiện này.

## Tóm tắt một dòng
Sự kiện `onhashchange` trong JavaScript cho phép bạn theo dõi thay đổi trong phần hash của URL để quản lý điều hướng trong các ứng dụng web mà không tải lại trang.