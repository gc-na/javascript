<!--
Meta Description: # Sự kiện Kéo Thả (DragEvent) trong JavaScript ## Tóm tắt Sự kiện Kéo Thả (DragEvent) trong JavaScript cho phép các nhà phát triển xác định và xử lý c...
Meta Keywords: kéo, thả, các, event, kiện
-->

# Sự kiện Kéo Thả (DragEvent) trong JavaScript

## Tóm tắt
Sự kiện Kéo Thả (DragEvent) trong JavaScript cho phép các nhà phát triển xác định và xử lý các thao tác kéo và thả trên các phần tử trong trang web, mang lại trải nghiệm tương tác phong phú cho người dùng.

## Tài liệu
### Mục đích
Sự kiện Kéo Thả (DragEvent) được sử dụng để quản lý các sự kiện liên quan đến kéo và thả, như bắt đầu kéo, kéo và thả một phần tử vào một vị trí khác trên trang.

### Cách sử dụng
Để sử dụng sự kiện DragEvent, bạn cần đăng ký các sự kiện như `dragstart`, `drag`, và `drop` cho các phần tử HTML. Các sự kiện này sẽ được kích hoạt khi người dùng thực hiện các thao tác kéo và thả.

### Cú pháp
```javascript
element.addEventListener('dragstart', function(event) {
    // Xử lý khi bắt đầu kéo
});

element.addEventListener('drag', function(event) {
    // Xử lý khi kéo
});

element.addEventListener('drop', function(event) {
    // Xử lý khi thả
    event.preventDefault(); // Ngăn chặn hành vi mặc định
});
```

### Thông tin chi tiết
- **Các thuộc tính của DragEvent**:
  - `dataTransfer`: Đối tượng này chứa thông tin về dữ liệu đang được kéo.
  - `clientX`, `clientY`: Tọa độ chuột khi sự kiện được kích hoạt.
  - `screenX`, `screenY`: Tọa độ trên màn hình.

## Ví dụ
### Ví dụ cơ bản
```html
<div id="drag" draggable="true">Kéo tôi!</div>
<div id="dropzone" style="width: 200px; height: 200px; border: 1px solid black;">Thả vào đây</div>

<script>
    const dragItem = document.getElementById('drag');
    const dropZone = document.getElementById('dropzone');

    dragItem.addEventListener('dragstart', function(event) {
        event.dataTransfer.setData('text/plain', 'Dữ liệu kéo');
    });

    dropZone.addEventListener('dragover', function(event) {
        event.preventDefault(); // Ngăn chặn hành vi mặc định để cho phép thả
    });

    dropZone.addEventListener('drop', function(event) {
        const data = event.dataTransfer.getData('text/plain');
        alert('Đã thả: ' + data);
    });
</script>
```

## Giải thích
### Những lưu ý phổ biến
- **Ngăn chặn hành vi mặc định**: Khi sử dụng sự kiện `drop`, bạn cần gọi `event.preventDefault()` để ngăn chặn hành vi mặc định của trình duyệt, cho phép thả dữ liệu vào khu vực mong muốn.
- **Thuộc tính draggable**: Để một phần tử có thể được kéo, bạn cần thiết lập thuộc tính `draggable` thành `true`.
- **Dữ liệu kéo**: Sử dụng đối tượng `dataTransfer` để lưu trữ và truy xuất dữ liệu trong quá trình kéo và thả.

## Tóm tắt một dòng
Sự kiện Kéo Thả (DragEvent) trong JavaScript cho phép xử lý các tác vụ kéo và thả, tạo ra các tương tác động cho người dùng trên trang web.