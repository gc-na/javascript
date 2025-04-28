<!--
Meta Description: # Sự Kiện ondragover trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ ## Tóm Tắt Sự kiện `ondragover` trong JavaScript cho phép bạn xử lý hành động kéo v...
Meta Keywords: kiện, thả, kéo, event, liệu
-->

# Sự Kiện ondragover trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ

## Tóm Tắt
Sự kiện `ondragover` trong JavaScript cho phép bạn xử lý hành động kéo và thả trong trình duyệt, xác định khu vực nào có thể nhận dữ liệu đang được kéo.

## Tài Liệu
Sự kiện `ondragover` được kích hoạt khi một đối tượng đang được kéo qua khu vực thả. Mục đích chính của sự kiện này là để cho phép các thao tác kéo và thả một cách trực quan, giúp người dùng biết rằng họ có thể thả dữ liệu vào khu vực đó.

### Cú pháp
```javascript
element.ondragover = function(event) {
    // Xử lý sự kiện kéo qua
};
```

### Chi Tiết
- **Đối tượng**: `event` là một đối tượng sự kiện, cho phép bạn kiểm soát hành vi của sự kiện kéo.
- **Ngăn chặn hành vi mặc định**: Để cho phép thả dữ liệu, bạn cần gọi `event.preventDefault()`. Nếu không, sự kiện `drop` sẽ không được kích hoạt.
- **Sự kiện liên quan**: `ondragenter`, `ondragleave`, và `ondrop` cũng là các sự kiện quan trọng trong quá trình kéo và thả.

## Ví Dụ
### Ví dụ 1: Khu vực thả đơn giản
```html
<div id="drop-zone" style="width: 300px; height: 300px; border: 2px dashed #ccc;">
    Kéo và thả vào đây
</div>

<script>
    const dropZone = document.getElementById('drop-zone');

    dropZone.ondragover = function(event) {
        event.preventDefault(); // Ngăn chặn hành vi mặc định
        dropZone.style.backgroundColor = '#f0f0f0'; // Thay đổi màu nền khi kéo qua
    };

    dropZone.ondragleave = function() {
        dropZone.style.backgroundColor = ''; // Đặt lại màu nền
    };

    dropZone.ondrop = function(event) {
        event.preventDefault();
        alert('Dữ liệu đã được thả!');
    };
</script>
```

### Ví dụ 2: Thả tệp tin
```html
<input type="file" id="fileInput" multiple>
<div id="fileDropZone" style="width: 300px; height: 300px; border: 2px solid #000;">
    Kéo và thả tệp vào đây
</div>

<script>
    const fileDropZone = document.getElementById('fileDropZone');

    fileDropZone.ondragover = function(event) {
        event.preventDefault(); // Ngăn chặn hành vi mặc định
    };

    fileDropZone.ondrop = function(event) {
        event.preventDefault();
        const files = event.dataTransfer.files;
        console.log('Tệp đã được thả:', files);
    };
</script>
```

## Giải Thích
- **Ngăn chặn hành vi mặc định**: Nếu bạn không gọi `event.preventDefault()`, trình duyệt sẽ xử lý sự kiện kéo mặc định, có thể gây ra sự cố trong ứng dụng của bạn.
- **Thời điểm kích hoạt**: Sự kiện `ondragover` sẽ được kích hoạt nhiều lần khi đối tượng kéo di chuyển qua khu vực thả, vì vậy hãy đảm bảo rằng mã xử lý sự kiện không gây ra lag hoặc giảm hiệu suất.
- **Thỏa thuận kiểu dữ liệu**: Bạn có thể kiểm tra kiểu dữ liệu của tệp tin hoặc dữ liệu được kéo trong sự kiện `ondrop` để xác định tính hợp lệ của dữ liệu.

## Tóm Tắt Một Dòng
Sự kiện `ondragover` trong JavaScript cho phép bạn xác định vùng thả cho các thao tác kéo và thả, giúp cải thiện trải nghiệm người dùng.