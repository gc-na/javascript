<!--
Meta Description: # Tập Trung (Focus) trong JavaScript: Hướng Dẫn Chi Tiết ## Tóm Tắt Trong JavaScript, "focus" là một thuộc tính quan trọng liên quan đến việc điều khi...
Meta Keywords: focus, phần, tập, trung, dùng
-->

# Tập Trung (Focus) trong JavaScript: Hướng Dẫn Chi Tiết

## Tóm Tắt
Trong JavaScript, "focus" là một thuộc tính quan trọng liên quan đến việc điều khiển sự tập trung của các phần tử trong giao diện người dùng (UI). Nó cho phép người dùng tương tác với các thành phần như ô nhập liệu, nút bấm và các phần tử khác trong trang web.

## Tài Liệu
### Mục Đích
Công dụng chính của `focus` trong JavaScript là để điều khiển việc tập trung của các phần tử DOM, giúp cải thiện trải nghiệm người dùng. Khi một phần tử có được sự tập trung, nó sẽ nhận được sự chú ý từ người dùng, cho phép họ nhập liệu hoặc tương tác với phần tử đó.

### Cách Sử Dụng
Để sử dụng `focus`, bạn có thể gọi phương thức `focus()` trên một phần tử DOM. Ví dụ, để tập trung vào một ô nhập liệu, bạn có thể thực hiện như sau:

```javascript
document.getElementById("myInput").focus();
```

### Chi Tiết
- **Phương thức**: `focus()` không nhận bất kỳ tham số nào.
- **Kết quả**: Khi phương thức này được gọi, phần tử sẽ trở thành phần tử đang được tập trung, và sẽ có thể nhận các sự kiện bàn phím.
- **Sự kiện liên quan**: Khi một phần tử nhận được sự tập trung, sự kiện `focus` sẽ được kích hoạt, và khi nó mất tập trung, sự kiện `blur` sẽ được gọi.

## Ví Dụ
### Ví dụ Cơ Bản
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ví dụ về Focus</title>
</head>
<body>
    <input type="text" id="myInput" placeholder="Nhập tên của bạn">
    <button onclick="setFocus()">Tập Trung</button>

    <script>
        function setFocus() {
            document.getElementById("myInput").focus();
        }
    </script>
</body>
</html>
```

### Tình Huống Thực Tế
Trong các ứng dụng web, bạn có thể tự động tập trung vào ô nhập liệu đầu tiên khi người dùng truy cập vào trang, như sau:

```javascript
window.onload = function() {
    document.getElementById("myInput").focus();
};
```

## Giải Thích
### Những Điều Cần Lưu Ý
- **Tương thích trình duyệt**: Hầu hết các trình duyệt hiện đại đều hỗ trợ phương thức `focus()`, nhưng có thể có sự khác biệt trong cách xử lý sự kiện `focus` và `blur`.
- **Không thể tập trung vào phần tử ẩn**: Nếu một phần tử không hiển thị (có thuộc tính `display: none`), việc gọi `focus()` trên nó sẽ không có tác dụng.
- **Sự tương tác của người dùng**: Một số trình duyệt có thể ngăn chặn việc tự động gọi `focus()` mà không có sự tương tác từ người dùng (ví dụ: nhấp chuột).

## Tóm Tắt Một Dòng
Trong JavaScript, `focus` là phương thức dùng để đặt sự tập trung vào phần tử DOM, giúp người dùng tương tác hiệu quả hơn với giao diện web.