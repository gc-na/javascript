<!--
Meta Description: # Sự kiện onmouseenter trong JavaScript: Hướng dẫn và Ví dụ ## Tóm tắt Sự kiện `onmouseenter` trong JavaScript là một sự kiện được sử dụng để phát hiệ...
Meta Keywords: onmouseenter, html, kiện, chuột, vào
-->

# Sự kiện onmouseenter trong JavaScript: Hướng dẫn và Ví dụ

## Tóm tắt
Sự kiện `onmouseenter` trong JavaScript là một sự kiện được sử dụng để phát hiện khi con trỏ chuột di chuyển vào bên trong một phần tử HTML cụ thể.

## Tài liệu
### Mục đích
Sự kiện `onmouseenter` được sử dụng để thực hiện hành động khi con trỏ chuột di chuyển vào một phần tử. Khác với sự kiện `onmouseover`, `onmouseenter` không kích hoạt khi con trỏ chuột di chuyển giữa các phần tử con của phần tử đang theo dõi.

### Cách sử dụng
Sự kiện `onmouseenter` có thể được thêm vào phần tử HTML thông qua thuộc tính `onmouseenter` trong thẻ HTML hoặc bằng cách sử dụng JavaScript để thêm sự kiện. 

**Cú pháp HTML:**
```html
<div onmouseenter="myFunction()">Di chuột vào đây</div>
```

**Cú pháp JavaScript:**
```javascript
const element = document.getElementById("myElement");
element.addEventListener("mouseenter", function() {
    // Hành động khi chuột di chuyển vào
});
```

### Chi tiết
- **Tham số:** Sự kiện này không nhận tham số nào.
- **Đối tượng sự kiện:** `event` là đối tượng sự kiện mà bạn có thể sử dụng để lấy thông tin về sự kiện (như vị trí chuột).
- **Hỗ trợ trình duyệt:** `onmouseenter` được hỗ trợ trên hầu hết các trình duyệt hiện đại.

## Ví dụ
### Ví dụ 1: Sử dụng onmouseenter trong HTML
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ví dụ onmouseenter</title>
</head>
<body>
    <div onmouseenter="alert('Chuột đã di chuyển vào!')">Di chuột vào đây</div>
</body>
</html>
```

### Ví dụ 2: Sử dụng onmouseenter trong JavaScript
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ví dụ onmouseenter</title>
</head>
<body>
    <div id="myElement">Di chuột vào đây</div>
    <script>
        const element = document.getElementById("myElement");
        element.addEventListener("mouseenter", function() {
            console.log("Chuột đã di chuyển vào!");
        });
    </script>
</body>
</html>
```

## Giải thích
- **Khác biệt với onmouseover:** `onmouseenter` chỉ kích hoạt khi chuột vào phần tử chính, trong khi `onmouseover` sẽ kích hoạt cả khi di chuyển giữa các phần tử con.
- **Tránh sử dụng nhiều lần:** Khi thêm nhiều sự kiện `onmouseenter` trên cùng một phần tử, bạn có thể gặp phải sự cố với việc gọi nhiều hàm không cần thiết.

## Tóm tắt một dòng
Sự kiện `onmouseenter` trong JavaScript cho phép bạn phát hiện khi con trỏ chuột di chuyển vào một phần tử mà không bị ảnh hưởng bởi các phần tử con bên trong.