<!--
Meta Description: # Sự kiện ondragstart trong JavaScript: Hướng dẫn chi tiết ## Tóm tắt Sự kiện `ondragstart` trong JavaScript được sử dụng để xác định khi một đối tượn...
Meta Keywords: kéo, kiện, ondragstart, event, trong
-->

# Sự kiện ondragstart trong JavaScript: Hướng dẫn chi tiết

## Tóm tắt
Sự kiện `ondragstart` trong JavaScript được sử dụng để xác định khi một đối tượng bắt đầu quá trình kéo thả. Đây là một phần quan trọng trong việc tạo ra các giao diện người dùng tương tác, cho phép người dùng kéo các phần tử và thả chúng tại vị trí khác trên trang web.

## Tài liệu
### Mục đích
Sự kiện `ondragstart` được kích hoạt khi người dùng bắt đầu kéo một phần tử. Nó cho phép bạn thực hiện các hành động trước khi phần tử được kéo đi, như thiết lập dữ liệu kéo hoặc thay đổi giao diện người dùng.

### Cách sử dụng
Bạn có thể sử dụng sự kiện `ondragstart` thông qua thuộc tính HTML hoặc thông qua JavaScript. Dưới đây là cú pháp cơ bản:

```html
<div draggable="true" ondragstart="myFunction(event)">Kéo tôi!</div>
```

Hoặc bằng JavaScript:

```javascript
const element = document.getElementById("myElement");
element.ondragstart = function(event) {
    myFunction(event);
};
```

### Chi tiết
- **draggable**: Thuộc tính này cần được đặt thành `true` trên phần tử mà bạn muốn kéo.
- **event**: Đối tượng sự kiện được truyền vào hàm xử lý, cho phép bạn truy cập thông tin về sự kiện kéo.

## Ví dụ
Dưới đây là một ví dụ đơn giản về cách sử dụng `ondragstart`:

```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sử dụng ondragstart</title>
    <style>
        #drag1 {
            width: 100px;
            height: 100px;
            background-color: blue;
            color: white;
            text-align: center;
            line-height: 100px;
            cursor: move;
        }
    </style>
</head>
<body>

<div id="drag1" draggable="true" ondragstart="drag(event)">Kéo tôi!</div>

<script>
function drag(event) {
    event.dataTransfer.setData("text", event.target.id);
}
</script>

</body>
</html>
```

Trong ví dụ này, khi người dùng kéo phần tử với ID `drag1`, một dữ liệu sẽ được thiết lập để chuyển đi cùng với sự kiện kéo.

## Giải thích
- **Lưu ý về trình duyệt**: Một số trình duyệt có thể không hỗ trợ đầy đủ các tính năng kéo thả, vì vậy bạn nên kiểm tra khả năng tương thích.
- **Dữ liệu kéo**: Bạn có thể sử dụng `event.dataTransfer` để thiết lập thông tin mà bạn muốn truyền đi trong quá trình kéo.
- **Ngăn chặn sự kiện**: Nếu bạn không muốn hành động kéo mặc định, hãy sử dụng `event.preventDefault()` trong hàm xử lý sự kiện.

## Tóm tắt một dòng
Sự kiện `ondragstart` trong JavaScript cho phép lập trình viên xử lý hành động khi một phần tử bắt đầu được kéo, mang lại sự linh hoạt trong việc tạo ra các giao diện kéo thả.