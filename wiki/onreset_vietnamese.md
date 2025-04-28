<!--
Meta Description: # Sự kiện onreset trong JavaScript: Hướng dẫn chi tiết và ví dụ ## Tóm tắt Sự kiện `onreset` trong JavaScript được sử dụng để xác định hành động khi m...
Meta Keywords: onreset, html, kiện, biểu, mẫu
-->

# Sự kiện onreset trong JavaScript: Hướng dẫn chi tiết và ví dụ

## Tóm tắt
Sự kiện `onreset` trong JavaScript được sử dụng để xác định hành động khi một biểu mẫu HTML được đặt lại. Hành động này thường xảy ra khi người dùng nhấn nút "Reset" trên biểu mẫu, giúp khôi phục các trường về trạng thái mặc định.

## Tài liệu
Sự kiện `onreset` là một phần của giao diện DOM (Document Object Model) trong JavaScript. Khi một biểu mẫu được đặt lại, sự kiện này sẽ được kích hoạt, cho phép lập trình viên thực hiện các hành động bổ sung như xác nhận hoặc thông báo cho người dùng.

### Mục đích
- Để xử lý sự kiện khôi phục trạng thái của biểu mẫu.
- Cung cấp một cách để thực hiện các hành động tùy chỉnh khi người dùng nhấn nút "Reset".

### Cách sử dụng
Sự kiện `onreset` có thể được gán trực tiếp trong HTML hoặc thông qua JavaScript. Dưới đây là cú pháp cơ bản:

```html
<form onreset="functionName()">
  <!-- Các trường nhập liệu -->
  <input type="text" name="username" />
  <input type="reset" value="Reset" />
</form>
```

Hoặc gán qua JavaScript:

```javascript
const form = document.querySelector('form');
form.onreset = function() {
  // Hành động khi biểu mẫu được đặt lại
};
```

## Ví dụ
### Ví dụ 1: Sử dụng `onreset` trong HTML
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ví dụ onreset</title>
</head>
<body>
    <form onreset="alert('Biểu mẫu đã được đặt lại!')">
        <input type="text" name="username" placeholder="Tên đăng nhập" />
        <input type="reset" value="Đặt lại" />
    </form>
</body>
</html>
```

### Ví dụ 2: Sử dụng `onreset` trong JavaScript
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ví dụ onreset với JavaScript</title>
</head>
<body>
    <form id="myForm">
        <input type="text" name="username" placeholder="Tên đăng nhập" />
        <input type="reset" value="Đặt lại" />
    </form>
    <script>
        const form = document.getElementById('myForm');
        form.onreset = function() {
            console.log('Biểu mẫu đã được đặt lại!');
        };
    </script>
</body>
</html>
```

## Giải thích
### Những cạm bẫy phổ biến
- **Không kích hoạt sự kiện**: Nếu bạn không nhận thấy sự kiện `onreset` được kích hoạt, hãy kiểm tra xem nút "Reset" có thuộc về biểu mẫu hay không.
- **Không có hành động bổ sung**: Nếu bạn không định nghĩa hành động gì trong sự kiện, người dùng sẽ không nhận thấy sự khác biệt khi biểu mẫu được đặt lại.

### Lưu ý
- Sự kiện này chỉ hoạt động với các biểu mẫu HTML, và không có hiệu lực với các thành phần khác.
- Nên sử dụng sự kiện này một cách hợp lý, vì việc đặt lại biểu mẫu sẽ loại bỏ tất cả giá trị đã nhập.

## Tóm tắt một câu
Sự kiện `onreset` trong JavaScript cho phép lập trình viên xử lý hành động khi một biểu mẫu HTML được đặt lại, giúp cải thiện trải nghiệm người dùng.