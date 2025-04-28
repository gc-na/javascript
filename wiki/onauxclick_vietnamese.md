<!--
Meta Description: # Sự kiện onauxclick trong JavaScript: Hướng dẫn chi tiết ## Tóm tắt Sự kiện `onauxclick` trong JavaScript là một sự kiện được kích hoạt khi người dùn...
Meta Keywords: kiện, chuột, nút, onauxclick, các
-->

# Sự kiện onauxclick trong JavaScript: Hướng dẫn chi tiết

## Tóm tắt
Sự kiện `onauxclick` trong JavaScript là một sự kiện được kích hoạt khi người dùng nhấp chuột bằng một nút khác ngoài nút chính (thường là nút trái). Thường được sử dụng để phát hiện các hành động chuột không thông thường, sự kiện này hỗ trợ các tương tác phong phú hơn trong các ứng dụng web.

## Tài liệu
Sự kiện `onauxclick` được sử dụng để theo dõi các nhấp chuột không phải là nhấp chuột chính (nút trái). Sự kiện này là một phần của giao diện DOM Events và có thể được áp dụng cho bất kỳ phần tử HTML nào. 

### Mục đích
Mục đích của sự kiện `onauxclick` là để cung cấp thông tin về các nhấp chuột bằng nút chuột phụ, như nút giữa hoặc nút phải.

### Cách sử dụng
Sự kiện `onauxclick` có thể được gán trực tiếp trong HTML hoặc qua JavaScript. Dưới đây là cú pháp cơ bản:

```html
<element onauxclick="functionName()">...</element>
```

Hoặc trong JavaScript:

```javascript
element.addEventListener('auxclick', function(event) {
    // Xử lý sự kiện ở đây
});
```

### Chi tiết
- **Tham số sự kiện**: Sự kiện `onauxclick` có một đối tượng sự kiện, trong đó chứa thông tin về hành động chuột như:
  - `button`: Chỉ số của nút chuột được nhấn (0 = trái, 1 = giữa, 2 = phải).
  - `clientX`, `clientY`: Tọa độ của con trỏ chuột khi nhấp.
  
- **Tương thích trình duyệt**: Hầu hết các trình duyệt hiện đại hỗ trợ sự kiện `onauxclick`, nhưng việc sử dụng nút chuột giữa có thể không phổ biến trên tất cả các thiết bị.

## Ví dụ
### Ví dụ cơ bản
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <title>Ví dụ onauxclick</title>
</head>
<body>

<div id="myElement" style="width: 200px; height: 200px; background-color: lightblue;">
    Nhấp chuột vào đây
</div>

<script>
    const myElement = document.getElementById('myElement');
    myElement.onauxclick = function(event) {
        console.log('Nút chuột nhấn:', event.button);
    };
</script>

</body>
</html>
```

### Ví dụ với addEventListener
```javascript
const myElement = document.getElementById('myElement');
myElement.addEventListener('auxclick', function(event) {
    alert('Bạn đã nhấp chuột bằng nút: ' + event.button);
});
```

## Giải thích
- **Nhầm lẫn với sự kiện khác**: Dễ nhầm lẫn giữa `onauxclick` với các sự kiện khác như `onclick`. Sự kiện `onclick` chỉ phản hồi nhấp chuột bằng nút chính.
- **Thiết bị không hỗ trợ**: Trên một số thiết bị, như điện thoại di động, sự kiện này có thể không hoạt động do sự khác biệt trong cách thức tương tác của người dùng.
- **Sự kiện không phải lúc nào cũng được kích hoạt**: Nếu người dùng nhấn nút trái chuột và kéo chuột, sự kiện `onauxclick` sẽ không được kích hoạt.

## Tóm tắt ngắn gọn
Sự kiện `onauxclick` trong JavaScript cho phép các nhà phát triển theo dõi hành động nhấp chuột bằng nút không chính, góp phần tạo ra các tương tác người dùng phong phú hơn trong ứng dụng web.