<!--
Meta Description: # HTMLSpanElement trong JavaScript: Tìm Hiểu và Cách Sử Dụng ## Tóm Tắt `HTMLSpanElement` là một giao diện trong DOM (Document Object Model) đại diện ...
Meta Keywords: span, phần, html, các, trong
-->

# HTMLSpanElement trong JavaScript: Tìm Hiểu và Cách Sử Dụng

## Tóm Tắt
`HTMLSpanElement` là một giao diện trong DOM (Document Object Model) đại diện cho phần tử `<span>` trong HTML. Nó cho phép lập trình viên truy cập và điều khiển các thuộc tính và phương thức của các phần tử `<span>` thông qua JavaScript.

## Tài Liệu
`HTMLSpanElement` là một phần tử inline trong HTML, thường được sử dụng để nhóm các đoạn văn bản hoặc nội dung khác mà không tạo ra ngắt dòng. Giao diện này cho phép bạn tương tác với các thuộc tính như `innerHTML`, `style`, và `className` của phần tử `<span>`. 

### Mục Đích
Mục đích chính của `HTMLSpanElement` là hỗ trợ việc định dạng và điều khiển các đoạn văn bản trong một tài liệu HTML mà không làm thay đổi cấu trúc của trang.

### Cách Sử Dụng
Bạn có thể tạo và truy cập các phần tử `<span>` bằng JavaScript như sau:

1. **Tạo phần tử `<span>` mới:**
   ```javascript
   const spanElement = document.createElement('span');
   spanElement.textContent = 'Đây là một đoạn văn bản.';
   document.body.appendChild(spanElement);
   ```

2. **Truy cập và thay đổi thuộc tính của phần tử `<span>`:**
   ```javascript
   const existingSpan = document.querySelector('span');
   existingSpan.style.color = 'red'; // Đổi màu chữ thành đỏ
   existingSpan.className = 'highlight'; // Thay đổi class
   ```

## Ví Dụ
Dưới đây là một số ví dụ minh họa về cách sử dụng `HTMLSpanElement` trong JavaScript:

### Ví dụ 1: Tạo và Thêm `<span>` vào Trang
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <title>Ví dụ HTMLSpanElement</title>
</head>
<body>
    <script>
        const span = document.createElement('span');
        span.textContent = 'Hello, World!';
        document.body.appendChild(span);
    </script>
</body>
</html>
```

### Ví dụ 2: Thay Đổi Thuộc Tính Của `<span>`
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <title>Thay Đổi Thuộc Tính</title>
</head>
<body>
    <span id="mySpan">Text ban đầu</span>
    <script>
        const span = document.getElementById('mySpan');
        span.style.fontWeight = 'bold'; // Đổi chữ thành đậm
        span.textContent = 'Text đã thay đổi'; // Thay đổi nội dung
    </script>
</body>
</html>
```

## Giải Thích
Khi làm việc với `HTMLSpanElement`, có một số điều bạn cần lưu ý:

- **Phần tử Inline:** `<span>` là phần tử inline, nghĩa là nó không tạo ra ngắt dòng trong tài liệu. Điều này có thể ảnh hưởng đến cách bố trí nội dung của bạn.
- **Tương tác với CSS:** Bạn có thể sử dụng các thuộc tính CSS để thay đổi cách hiển thị của phần tử `<span>`, nhưng cần đảm bảo rằng các thuộc tính CSS này không gây ra xung đột với các phần tử khác trên trang.
- **Truy cập Nhanh:** Sử dụng các phương thức như `getElementById()` hoặc `querySelector()` để truy cập nhanh chóng các phần tử `<span>` trong DOM.

## Tóm Tắt Một Câu
`HTMLSpanElement` là một giao diện trong JavaScript cho phép lập trình viên tạo và điều khiển các phần tử `<span>` trong tài liệu HTML, giúp định dạng và quản lý nội dung hiệu quả.