<!--
Meta Description: # Tệp trong JavaScript: Cách làm việc với File API ## Tóm tắt Tệp (File) trong JavaScript là một đối tượng quan trọng cho phép lập trình viên làm việc...
Meta Keywords: tệp, file, trong, javascript, các
-->

# Tệp trong JavaScript: Cách làm việc với File API

## Tóm tắt
Tệp (File) trong JavaScript là một đối tượng quan trọng cho phép lập trình viên làm việc với dữ liệu tệp trong trình duyệt, hỗ trợ các chức năng như tải lên, đọc và xử lý tệp.

## Tài liệu
### Mục đích
Đối tượng `File` trong JavaScript đại diện cho một tệp được chọn từ hệ thống tệp của người dùng. Nó thường được sử dụng trong các ứng dụng web để cho phép người dùng tải lên và xử lý tệp, chẳng hạn như hình ảnh, văn bản hoặc các định dạng tệp khác.

### Cách sử dụng
Đối tượng `File` có thể được truy cập thông qua đối tượng `FileList`, mà bạn có thể nhận được từ một thẻ `<input>` có thuộc tính `type="file"`. Khi người dùng chọn tệp, bạn có thể truy cập các thông tin như tên tệp, kích thước và kiểu tệp.

#### Cú pháp
```javascript
let inputElement = document.querySelector('input[type="file"]');
let fileList = inputElement.files; // Trả về một danh sách các tệp được chọn
```

### Chi tiết
- **Thuộc tính**:
  - `name`: Tên của tệp.
  - `size`: Kích thước của tệp tính bằng byte.
  - `type`: Loại MIME của tệp.
  - `lastModified`: Thời gian tệp được sửa đổi lần cuối.

- **Phương thức**:
  - `slice()`: Cho phép tách một phần của tệp để xử lý.

## Ví dụ
### Ví dụ 1: Lấy thông tin tệp
```javascript
document.querySelector('input[type="file"]').addEventListener('change', function(event) {
    let file = event.target.files[0];
    console.log('Tên tệp:', file.name);
    console.log('Kích thước:', file.size);
    console.log('Loại:', file.type);
});
```

### Ví dụ 2: Đọc nội dung tệp
```javascript
let inputElement = document.querySelector('input[type="file"]');
inputElement.addEventListener('change', function(event) {
    let file = event.target.files[0];
    let reader = new FileReader();

    reader.onload = function(e) {
        console.log('Nội dung tệp:', e.target.result);
    };

    reader.readAsText(file); // Đọc dưới dạng văn bản
});
```

## Giải thích
- **Lỗi thường gặp**:
  - Không kiểm tra xem người dùng đã chọn tệp hay chưa trước khi cố gắng truy cập thông tin tệp.
  - Không xử lý các loại tệp không hợp lệ có thể dẫn đến lỗi khi đọc tệp.

- **Ghi chú**:
  - File API chỉ hoạt động trong môi trường trình duyệt và không thể sử dụng trong Node.js hoặc các môi trường không có giao diện người dùng.
  - Đảm bảo rằng bạn kiểm tra loại tệp trước khi xử lý để tránh lỗi không mong muốn.

## Tóm tắt một dòng
Đối tượng `File` trong JavaScript cho phép bạn truy cập và xử lý tệp được chọn từ hệ thống tệp của người dùng trong trình duyệt.