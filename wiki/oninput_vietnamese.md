<!--
Meta Description: # Sự kiện oninput trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ ## Tóm tắt Sự kiện `oninput` trong JavaScript là một sự kiện được kích hoạt khi giá tr...
Meta Keywords: kiện, oninput, các, trong, javascript
-->

# Sự kiện oninput trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ

## Tóm tắt
Sự kiện `oninput` trong JavaScript là một sự kiện được kích hoạt khi giá trị của một phần tử input thay đổi, giúp lập trình viên theo dõi các thay đổi trong thời gian thực ngay khi người dùng nhập liệu.

## Tài liệu
Sự kiện `oninput` là một phần của các sự kiện tương tác trong JavaScript, thường được sử dụng với các phần tử HTML như `<input>`, `<textarea>`, và một số phần tử khác. Mục đích chính của sự kiện này là theo dõi và phản hồi lại các thay đổi của người dùng khi họ nhập dữ liệu vào các trường nhập liệu.

### Cú pháp
Có thể sử dụng sự kiện `oninput` theo hai cách:

1. **Qua HTML**:
   ```html
   <input type="text" oninput="functionName()">
   ```

2. **Qua JavaScript**:
   ```javascript
   document.getElementById('elementId').oninput = function() {
       // Xử lý sự kiện
   };
   ```

### Chi tiết
- **Đối tượng sự kiện**: Khi sự kiện `oninput` xảy ra, nó sẽ tạo ra một đối tượng sự kiện mà bạn có thể sử dụng để lấy thông tin chi tiết về sự kiện.
- **Gọi hàm**: Bạn có thể gọi một hàm JavaScript để xử lý sự kiện này, cho phép bạn thực hiện các hành động như xác thực dữ liệu hoặc cập nhật giao diện người dùng trong thời gian thực.

## Ví dụ
### Ví dụ Cơ Bản
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sự kiện oninput</title>
</head>
<body>
    <label for="username">Nhập tên người dùng:</label>
    <input type="text" id="username" oninput="updateText()">
    <p id="output"></p>

    <script>
        function updateText() {
            const input = document.getElementById('username').value;
            document.getElementById('output').innerText = input;
        }
    </script>
</body>
</html>
```

## Giải thích
### Những điều cần lưu ý
- **Hỗ trợ trình duyệt**: Sự kiện `oninput` được hỗ trợ trên hầu hết các trình duyệt hiện đại, nhưng nếu bạn cần hỗ trợ cho các trình duyệt cũ hơn, hãy xem xét sử dụng sự kiện `onchange` hoặc `onkeydown`.
- **Hiệu suất**: Nếu hàm được gọi có nhiều tác vụ nặng, có thể gây ra độ trễ trong trải nghiệm người dùng. Nên tối ưu hóa mã để tránh giảm hiệu suất.
- **Không giống như onchange**: Sự kiện `oninput` sẽ được kích hoạt ngay khi giá trị thay đổi, trong khi `onchange` chỉ được gọi khi người dùng rời khỏi trường nhập liệu.

## Tóm tắt một dòng
Sự kiện `oninput` trong JavaScript cho phép theo dõi và phản hồi ngay lập tức các thay đổi trong giá trị của các phần tử nhập liệu, tạo ra trải nghiệm người dùng mượt mà hơn.