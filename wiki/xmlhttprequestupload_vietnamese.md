<!--
Meta Description: # XMLHttpRequestUpload trong JavaScript: Hướng Dẫn Chi Tiết ## Tóm Tắt `XMLHttpRequestUpload` là một đối tượng trong JavaScript được sử dụng để quản l...
Meta Keywords: tải, lên, xhr, trình, upload
-->

# XMLHttpRequestUpload trong JavaScript: Hướng Dẫn Chi Tiết

## Tóm Tắt
`XMLHttpRequestUpload` là một đối tượng trong JavaScript được sử dụng để quản lý việc tải lên dữ liệu thông qua đối tượng `XMLHttpRequest`. Nó cho phép bạn theo dõi tiến trình tải lên và xử lý các sự kiện liên quan đến tải lên.

## Tài Liệu
### Mục Đích
`XMLHttpRequestUpload` được thiết kế để cung cấp một cách dễ dàng để theo dõi các sự kiện liên quan đến quá trình tải lên dữ liệu, chẳng hạn như khi bắt đầu tải lên, khi đang tải lên và khi tải lên hoàn tất. Đối tượng này có thể được sử dụng cùng với đối tượng `XMLHttpRequest` để thực hiện các yêu cầu HTTP.

### Cách Sử Dụng
Để sử dụng `XMLHttpRequestUpload`, bạn cần tạo một đối tượng `XMLHttpRequest`, sau đó sử dụng thuộc tính `upload` của nó để truy cập vào đối tượng `XMLHttpRequestUpload`. Bạn có thể thêm các sự kiện như `progress`, `load`, và `error` để theo dõi quá trình tải lên.

```javascript
const xhr = new XMLHttpRequest();
const formData = new FormData(document.querySelector('form'));

xhr.open('POST', 'upload_url');

xhr.upload.addEventListener('progress', function(e) {
    if (e.lengthComputable) {
        const percentComplete = (e.loaded / e.total) * 100;
        console.log(`Đang tải lên: ${percentComplete}%`);
    }
}, false);

xhr.upload.addEventListener('load', function() {
    console.log('Tải lên hoàn tất!');
}, false);

xhr.upload.addEventListener('error', function() {
    console.error('Đã xảy ra lỗi trong quá trình tải lên.');
}, false);

xhr.send(formData);
```

## Ví Dụ
### Ví Dụ Cơ Bản
Dưới đây là một ví dụ đơn giản về cách sử dụng `XMLHttpRequestUpload` để tải lên một tệp:

```html
<form id="uploadForm">
    <input type="file" name="file" id="fileInput">
    <button type="submit">Tải lên</button>
</form>

<script>
document.getElementById('uploadForm').onsubmit = function(event) {
    event.preventDefault();
    
    const xhr = new XMLHttpRequest();
    const formData = new FormData(this);
    
    xhr.open('POST', '/upload');

    xhr.upload.addEventListener('progress', function(e) {
        if (e.lengthComputable) {
            const percentComplete = (e.loaded / e.total) * 100;
            console.log(`Đang tải lên: ${percentComplete}%`);
        }
    });

    xhr.upload.addEventListener('load', function() {
        console.log('Tải lên hoàn tất!');
    });

    xhr.upload.addEventListener('error', function() {
        console.error('Đã xảy ra lỗi trong quá trình tải lên.');
    });

    xhr.send(formData);
};
</script>
```

## Giải Thích
### Những Cái Bẫy Thường Gặp
- **Không Kiểm Tra Kích Thước Tệp**: Trước khi tải lên, hãy đảm bảo kiểm tra kích thước và định dạng của tệp để tránh tải lên các tệp không hợp lệ.
- **Kết Nối Internet Không Ổn Định**: Trong trường hợp mạng không ổn định, bạn có thể gặp phải lỗi trong quá trình tải lên. Đảm bảo xử lý các sự kiện `error` và `abort`.
- **Chưa Đảm Bảo Xử Lý Phản Hồi**: Đừng quên xử lý phản hồi từ máy chủ sau khi hoàn tất tải lên để biết liệu quá trình có thành công hay không.

## Tóm Tắt Một Dòng
`XMLHttpRequestUpload` là một đối tượng JavaScript cho phép theo dõi và quản lý quá trình tải lên dữ liệu qua `XMLHttpRequest`.