<!--
Meta Description: # Sự kiện onselectionchange trong JavaScript: Cách sử dụng và ví dụ ## Tóm tắt Sự kiện `onselectionchange` trong JavaScript được sử dụng để theo dõi t...
Meta Keywords: chọn, kiện, trong, html, option
-->

# Sự kiện onselectionchange trong JavaScript: Cách sử dụng và ví dụ

## Tóm tắt
Sự kiện `onselectionchange` trong JavaScript được sử dụng để theo dõi thay đổi lựa chọn của người dùng trên trang web, cho phép lập trình viên phản hồi nhanh chóng khi người dùng thay đổi lựa chọn trong các phần tử như văn bản, dropdowns hoặc các thành phần khác.

## Tài liệu
### Mục đích
`onselectionchange` là một sự kiện rất hữu ích trong JavaScript, giúp lập trình viên phát hiện và xử lý các thay đổi trong lựa chọn của người dùng. Sự kiện này thường được sử dụng trong các ứng dụng web, đặc biệt là khi làm việc với các form hoặc các phần tử tương tác.

### Cách sử dụng
Sự kiện `onselectionchange` có thể được gán trực tiếp vào các phần tử HTML hoặc thông qua JavaScript. Để sử dụng sự kiện này, bạn có thể thêm một trình xử lý sự kiện vào phần tử mà bạn muốn theo dõi.

Ví dụ:
```html
<select id="mySelect" onchange="handleSelectionChange()">
  <option value="1">Tùy chọn 1</option>
  <option value="2">Tùy chọn 2</option>
</select>
```

```javascript
function handleSelectionChange() {
  const selectElement = document.getElementById("mySelect");
  console.log("Giá trị đã chọn: " + selectElement.value);
}
```

## Ví dụ
### Ví dụ 1: Sử dụng với một dropdown
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ví dụ onselectionchange</title>
</head>
<body>
    <select id="fruitSelect" onchange="updateSelection()">
        <option value="apple">Táo</option>
        <option value="banana">Chuối</option>
        <option value="orange">Cam</option>
    </select>
    <p id="selectedFruit">Bạn đã chọn: </p>

    <script>
        function updateSelection() {
            const select = document.getElementById("fruitSelect");
            const display = document.getElementById("selectedFruit");
            display.textContent = "Bạn đã chọn: " + select.value;
        }
    </script>
</body>
</html>
```

### Ví dụ 2: Theo dõi lựa chọn văn bản
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ví dụ onselectionchange với văn bản</title>
</head>
<body>
    <textarea id="myTextArea" rows="4" cols="50" onselect="handleTextSelection()"></textarea>
    <p id="selectionInfo">Lựa chọn của bạn: </p>

    <script>
        function handleTextSelection() {
            const textArea = document.getElementById("myTextArea");
            const selection = textArea.value.substring(textArea.selectionStart, textArea.selectionEnd);
            document.getElementById("selectionInfo").textContent = "Lựa chọn của bạn: " + selection;
        }
    </script>
</body>
</html>
```

## Giải thích
### Những điểm cần lưu ý
- Sự kiện `onselectionchange` không phải là một sự kiện tiêu chuẩn trong HTML5, và vì thế, không phải mọi trình duyệt đều hỗ trợ nó. Hãy kiểm tra tính tương thích trước khi sử dụng.
- Đảm bảo rằng bạn đã gán đúng trình xử lý sự kiện cho phần tử mà bạn muốn theo dõi.
- Các thay đổi trong lựa chọn có thể không được phát hiện nếu chúng xảy ra quá nhanh hoặc nếu không có sự thay đổi thực sự trong lựa chọn.

## Tóm tắt một dòng
Sự kiện `onselectionchange` trong JavaScript cho phép lập trình viên theo dõi và xử lý thay đổi lựa chọn của người dùng trên các phần tử giao diện.