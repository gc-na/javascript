<!--
Meta Description: # Sự kiện onkeydown trong JavaScript: Hướng dẫn và Ví dụ ## Tóm tắt Sự kiện `onkeydown` trong JavaScript là một trong những sự kiện liên quan đến bàn ...
Meta Keywords: phím, onkeydown, trong, html, được
-->

# Sự kiện onkeydown trong JavaScript: Hướng dẫn và Ví dụ

## Tóm tắt
Sự kiện `onkeydown` trong JavaScript là một trong những sự kiện liên quan đến bàn phím, cho phép lập trình viên theo dõi khi một phím được nhấn xuống trong quá trình tương tác với trang web.

## Tài liệu
Sự kiện `onkeydown` được sử dụng để phát hiện khi người dùng nhấn một phím trên bàn phím. Sự kiện này sẽ được kích hoạt ngay khi phím được nhấn xuống, trước khi nó được thả ra. Điều này cho phép bạn xử lý các hành động ngay lập tức, chẳng hạn như điều hướng trong một trò chơi, nhập liệu trong một form, hoặc thực hiện các chức năng khác liên quan đến bàn phím.

### Cú pháp
Sự kiện `onkeydown` có thể được sử dụng trong HTML hoặc JavaScript. Dưới đây là cú pháp cơ bản:

1. **HTML:**
   ```html
   <input type="text" onkeydown="yourFunction(event)">
   ```

2. **JavaScript:**
   ```javascript
   document.addEventListener('keydown', function(event) {
       // Xử lý sự kiện ở đây
   });
   ```

### Tham số
- **event**: Đối tượng sự kiện chứa thông tin về phím được nhấn, bao gồm mã phím (key code), giá trị phím (key value), và trạng thái của các phím điều chỉnh (shift, ctrl, alt).

## Ví dụ
### Ví dụ 1: Sử dụng onkeydown trong HTML
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ví dụ onkeydown</title>
</head>
<body>
    <input type="text" onkeydown="alert('Bạn đã nhấn phím!')">
</body>
</html>
```

### Ví dụ 2: Sử dụng onkeydown trong JavaScript
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ví dụ onkeydown với JavaScript</title>
</head>
<body>
    <input type="text" id="myInput">
    <script>
        document.getElementById('myInput').addEventListener('keydown', function(event) {
            console.log('Phím vừa nhấn: ' + event.key);
        });
    </script>
</body>
</html>
```

## Giải thích
Khi sử dụng `onkeydown`, có một số điểm cần lưu ý:
- **Tốc độ xử lý**: Sự kiện `onkeydown` được kích hoạt ngay khi phím được nhấn, do đó bạn nên xử lý các tác vụ nhẹ để tránh làm chậm trải nghiệm người dùng.
- **Phím điều chỉnh**: Để kiểm tra xem một phím điều chỉnh như Shift, Ctrl hay Alt có đang được nhấn hay không, bạn có thể kiểm tra thuộc tính `event.shiftKey`, `event.ctrlKey`, hoặc `event.altKey`.
- **Mã phím**: Sử dụng `event.key` để lấy giá trị phím mà người dùng đã nhấn thay vì `event.keyCode`, vì `keyCode` đã được khuyến nghị không sử dụng trong các phiên bản mới của JavaScript.

## Tóm tắt một dòng
Sự kiện `onkeydown` trong JavaScript cho phép theo dõi và xử lý hành động nhấn phím ngay lập tức, giúp cải thiện trải nghiệm người dùng trong các ứng dụng web.