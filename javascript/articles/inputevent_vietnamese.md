<!--
Meta Description: # Sự kiện InputEvent trong JavaScript: Cách Sử Dụng và Ví Dụ ## Tóm tắt Sự kiện `InputEvent` trong JavaScript được sử dụng để theo dõi và xử lý các th...
Meta Keywords: kiện, các, trong, inputevent, thay
-->

# Sự kiện InputEvent trong JavaScript: Cách Sử Dụng và Ví Dụ

## Tóm tắt
Sự kiện `InputEvent` trong JavaScript được sử dụng để theo dõi và xử lý các thay đổi trong các phần tử nhập liệu như ô văn bản, textarea và các loại input khác.

## Tài liệu
### Mục đích
`InputEvent` là một sự kiện trong JavaScript được kích hoạt khi giá trị của một phần tử nhập liệu thay đổi. Điều này có thể xảy ra khi người dùng nhập liệu, dán văn bản, hoặc thay đổi giá trị bằng các phương thức khác. Sự kiện này giúp các nhà phát triển ứng dụng web có thể phản ứng ngay lập tức với các thay đổi trong dữ liệu nhập từ người dùng.

### Cách sử dụng
Để sử dụng `InputEvent`, bạn cần lắng nghe sự kiện này trên một phần tử HTML. Bạn có thể sử dụng phương thức `addEventListener` để đăng ký sự kiện.

```javascript
const inputElement = document.getElementById('myInput');

inputElement.addEventListener('input', function(event) {
    console.log('Giá trị hiện tại: ', event.target.value);
});
```

### Chi tiết
- **Tính năng**: `InputEvent` có thể được sử dụng trên hầu hết các phần tử nhập liệu như `<input>`, `<textarea>`, và `<select>`.
- **Các thuộc tính quan trọng**:
  - `data`: Chuỗi chứa dữ liệu mới được nhập vào.
  - `inputType`: Loại thao tác đã được thực hiện (ví dụ: "insertText", "deleteContentBackward").
  - `target`: Phần tử mà sự kiện đang được kích hoạt.

## Ví dụ
### Ví dụ 1: Theo dõi sự thay đổi trong ô văn bản
```html
<input type="text" id="myInput" placeholder="Nhập văn bản ở đây">
<script>
    const inputElement = document.getElementById('myInput');
    inputElement.addEventListener('input', function(event) {
        console.log('Giá trị hiện tại: ', event.target.value);
    });
</script>
```

### Ví dụ 2: Thay đổi giá trị với sự kiện `InputEvent`
```html
<textarea id="myTextarea" placeholder="Nhập nội dung ở đây"></textarea>
<script>
    const textareaElement = document.getElementById('myTextarea');
    textareaElement.addEventListener('input', function(event) {
        console.log('Nội dung hiện tại: ', event.target.value);
    });
</script>
```

## Giải thích
### Những điểm cần lưu ý
- **Trình duyệt hỗ trợ**: Hầu hết các trình duyệt hiện đại đều hỗ trợ `InputEvent`. Tuy nhiên, hãy kiểm tra khả năng tương thích nếu bạn cần hỗ trợ trình duyệt cũ.
- **Sự kiện `input` vs `change`**: Sự kiện `input` được kích hoạt ngay khi có sự thay đổi trong giá trị, trong khi `change` chỉ được kích hoạt khi phần tử mất tiêu điểm và giá trị đã thay đổi.
- **Hiệu suất**: Khi sử dụng `InputEvent`, hãy lưu ý đến hiệu suất, đặc biệt khi thực hiện các thao tác nặng trong trình xử lý sự kiện.

## Tóm tắt một dòng
Sự kiện `InputEvent` trong JavaScript cho phép theo dõi và phản ứng ngay lập tức với các thay đổi giá trị trong các phần tử nhập liệu.