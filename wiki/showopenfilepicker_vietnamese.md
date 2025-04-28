<!--
Meta Description: # Hướng Dẫn Sử Dụng showOpenFilePicker trong JavaScript ## Tóm Tắt `showOpenFilePicker` là một phương thức trong JavaScript cho phép người dùng mở hộp...
Meta Keywords: tệp, một, người, dùng, chọn
-->

# Hướng Dẫn Sử Dụng showOpenFilePicker trong JavaScript

## Tóm Tắt
`showOpenFilePicker` là một phương thức trong JavaScript cho phép người dùng mở hộp thoại chọn tệp. Tính năng này giúp cải thiện trải nghiệm người dùng trong các ứng dụng web bằng cách cho phép họ dễ dàng chọn tệp từ hệ thống của mình.

## Tài Liệu
### Mục Đích
`showOpenFilePicker` được thiết kế để cho phép người dùng lựa chọn một hoặc nhiều tệp từ máy tính của họ. Phương thức này là một phần của API File System Access, cho phép các ứng dụng web truy cập vào tệp và thư mục trên máy tính của người dùng một cách an toàn và dễ dàng.

### Cách Sử Dụng
Để sử dụng `showOpenFilePicker`, bạn cần gọi phương thức này trên đối tượng `window`. Phương thức trả về một Promise, cung cấp một mảng các tệp mà người dùng đã chọn.

### Cú Pháp
```javascript
let fileHandle = await window.showOpenFilePicker(options);
```
#### Tham Số
- `options` (tùy chọn): Một đối tượng tùy chọn cho phép bạn chỉ định các thuộc tính như `types` (các loại tệp được chấp nhận) và `multiple` (có cho phép chọn nhiều tệp hay không).

### Trả Về
- Phương thức trả về một Promise chứa một mảng các `FileSystemFileHandle`, đại diện cho các tệp mà người dùng đã chọn.

## Ví Dụ
### Ví Dụ Cơ Bản
```javascript
async function openFile() {
    try {
        const [fileHandle] = await window.showOpenFilePicker({
            types: [{
                description: 'Image Files',
                accept: {
                    'image/*': ['.png', '.jpg', '.jpeg', '.gif']
                }
            }],
            multiple: false
        });
        
        // Xử lý tệp đã chọn
        const file = await fileHandle.getFile();
        console.log('Tệp được chọn:', file.name);
    } catch (error) {
        console.error('Lỗi khi mở tệp:', error);
    }
}
```

## Giải Thích
- **Cảnh Báo**: Không phải tất cả các trình duyệt đều hỗ trợ API File System Access, vì vậy hãy kiểm tra tính khả dụng trước khi sử dụng `showOpenFilePicker`.
- **Quyền Truy Cập**: Người dùng cần cấp quyền cho ứng dụng web của bạn để truy cập vào tệp của họ. Điều này có thể yêu cầu sự cho phép từ người dùng.
- **Lỗi Thực Thi**: Nếu người dùng hủy bỏ phương thức, Promise sẽ bị từ chối với một lỗi. Bạn nên xử lý lỗi này để tránh làm ngưng trệ trải nghiệm người dùng.

## Tóm Tắt Một Dòng
`showOpenFilePicker` là một phương thức hữu ích trong JavaScript cho phép người dùng chọn tệp từ máy tính của họ, cải thiện trải nghiệm tương tác trong ứng dụng web.