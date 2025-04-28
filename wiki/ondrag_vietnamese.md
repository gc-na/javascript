<!--
Meta Description: # Sự kiện ondrag trong JavaScript: Hướng dẫn chi tiết ## Tóm tắt Sự kiện `ondrag` trong JavaScript cho phép bạn xử lý các hành động kéo thả (drag and ...
Meta Keywords: kéo, kiện, ondrag, event, thả
-->

# Sự kiện ondrag trong JavaScript: Hướng dẫn chi tiết

## Tóm tắt
Sự kiện `ondrag` trong JavaScript cho phép bạn xử lý các hành động kéo thả (drag and drop) của người dùng, góp phần tạo ra các giao diện tương tác linh hoạt và hấp dẫn.

## Tài liệu
Sự kiện `ondrag` được kích hoạt khi một phần tử đang được kéo. Nó là một trong những sự kiện quan trọng trong API kéo và thả của HTML5. Sự kiện này thường được sử dụng trong các ứng dụng web mà người dùng cần kéo và thả các phần tử, như trong danh sách, hình ảnh, hoặc thẻ.

### Mục đích
Mục đích chính của `ondrag` là để thông báo cho ứng dụng khi một phần tử đang được kéo, từ đó bạn có thể thực hiện các hành động phù hợp như cập nhật giao diện hoặc ghi lại trạng thái.

### Cách sử dụng
Để sử dụng sự kiện `ondrag`, bạn cần thêm nó vào phần tử HTML mà bạn muốn cho phép kéo thả. Dưới đây là cú pháp cơ bản:

```html
<div id="draggable" draggable="true" ondrag="handleDrag(event)">
  Kéo tôi
</div>
```

Trong đoạn mã trên, thuộc tính `draggable="true"` cho phép phần tử trở thành có thể kéo được. Hàm `handleDrag(event)` sẽ được gọi mỗi khi sự kiện `ondrag` xảy ra.

### Thông tin chi tiết
- **Tham số**: Sự kiện `ondrag` nhận một đối tượng sự kiện duy nhất.
- **Trả về**: Không có giá trị trả về.
- **Hỗ trợ**: `ondrag` được hỗ trợ trên hầu hết các trình duyệt hiện đại.

## Ví dụ
### Ví dụ 1: Sử dụng sự kiện ondrag cơ bản
```html
<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Kéo Thả</title>
</head>
<body>

<div id="draggable" draggable="true" ondrag="handleDrag(event)" style="width:100px; height:100px; background-color:blue;">
  Kéo tôi
</div>

<script>
  function handleDrag(event) {
    console.log("Đang kéo phần tử");
  }
</script>

</body>
</html>
```

### Ví dụ 2: Kéo và thả với thông báo
```html
<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Kéo và Thả</title>
</head>
<body>

<div id="draggable" draggable="true" ondrag="handleDrag(event)" style="width:100px; height:100px; background-color:green;">
  Kéo tôi
</div>

<div id="dropZone" ondragover="allowDrop(event)" ondrop="drop(event)" style="width:200px; height:200px; border:2px dashed black;">
  Thả vào đây
</div>

<script>
  function handleDrag(event) {
    console.log("Đang kéo phần tử");
  }

  function allowDrop(event) {
    event.preventDefault();
  }

  function drop(event) {
    event.preventDefault();
    console.log("Phần tử đã được thả");
  }
</script>

</body>
</html>
```

## Giải thích
Một số vấn đề thường gặp khi làm việc với sự kiện `ondrag` bao gồm:
- **Không kích hoạt**: Đảm bảo rằng thuộc tính `draggable` được đặt là `true` cho phần tử mà bạn muốn kéo.
- **Sự kiện không được xử lý**: Đảm bảo rằng các hàm bạn định nghĩa cho sự kiện được gọi chính xác và không gặp lỗi.
- **Thiếu sự kiện ondrop**: Nếu bạn muốn thực hiện hành động khi thả phần tử, bạn cần thêm sự kiện `ondrop` để xử lý.

## Tóm tắt một dòng
Sự kiện `ondrag` trong JavaScript cho phép theo dõi hành động kéo thả của người dùng, giúp tạo ra các giao diện tương tác mượt mà.