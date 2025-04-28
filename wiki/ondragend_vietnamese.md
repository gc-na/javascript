<!--
Meta Description: # Sự kiện ondragend trong JavaScript: Hướng dẫn và Ví dụ ## Tóm tắt Sự kiện `ondragend` trong JavaScript được kích hoạt khi quá trình kéo thả hoàn tất...
Meta Keywords: kéo, kiện, ondragend, thả, khi
-->

# Sự kiện ondragend trong JavaScript: Hướng dẫn và Ví dụ

## Tóm tắt
Sự kiện `ondragend` trong JavaScript được kích hoạt khi quá trình kéo thả hoàn tất. Nó cho phép lập trình viên xử lý các hành động cần thiết sau khi người dùng đã thả một đối tượng đã kéo.

## Tài liệu
Sự kiện `ondragend` là một trong những sự kiện của HTML5 Drag and Drop API. Sự kiện này xảy ra khi người dùng thả một phần tử sau khi kéo nó. Mục đích chính của `ondragend` là để thực hiện các hành động cần thiết sau khi kết thúc quá trình kéo.

### Cú pháp
```javascript
element.ondragend = function(event) {
    // Xử lý logic sau khi kéo thả
};
```

### Tham số
- `event`: Đối tượng sự kiện chứa thông tin về sự kiện kéo thả, bao gồm vị trí của con trỏ chuột và các thông tin khác liên quan đến phần tử.

### Các thuộc tính quan trọng
- `dataTransfer`: Đối tượng cho phép bạn lưu trữ dữ liệu trong quá trình kéo thả.

## Ví dụ
Dưới đây là một ví dụ đơn giản về cách sử dụng sự kiện `ondragend`:

```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <title>Ví dụ ondragend</title>
    <style>
        #dragItem {
            width: 100px;
            height: 100px;
            background-color: red;
            color: white;
            text-align: center;
            line-height: 100px;
            cursor: move;
        }
    </style>
</head>
<body>

<div id="dragItem" draggable="true">Kéo tôi</div>

<script>
    const dragItem = document.getElementById("dragItem");

    dragItem.ondragend = function(event) {
        alert("Kéo thả hoàn tất!");
    };
</script>

</body>
</html>
```

## Giải thích
Khi sử dụng sự kiện `ondragend`, có một số điều cần lưu ý:
- Đảm bảo rằng phần tử được kéo có thuộc tính `draggable` được đặt là `true`.
- Sự kiện `ondragend` chỉ hoạt động khi quá trình kéo thả thực sự diễn ra. Nếu bạn không thực hiện kéo hoặc thả, sự kiện này sẽ không được kích hoạt.
- Có thể kết hợp với các sự kiện khác như `ondragstart`, `ondragover` để tạo ra trải nghiệm kéo thả hoàn chỉnh.

## Tóm tắt một dòng
Sự kiện `ondragend` trong JavaScript cho phép xử lý các hành động cần thiết sau khi thực hiện kéo thả một phần tử.