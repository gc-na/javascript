<!--
Meta Description: # FileSystemWritableFileStream trong JavaScript: Ghi Dữ Liệu Vào Tệp Tin ## Tóm Tắt `FileSystemWritableFileStream` là một API trong JavaScript cho phé...
Meta Keywords: tệp, await, ghi, liệu, tin
-->

# FileSystemWritableFileStream trong JavaScript: Ghi Dữ Liệu Vào Tệp Tin

## Tóm Tắt
`FileSystemWritableFileStream` là một API trong JavaScript cho phép người dùng ghi dữ liệu vào tệp tin trên hệ thống tệp của trình duyệt, mang lại khả năng quản lý tệp tin một cách linh hoạt và hiệu quả.

## Tài Liệu
`FileSystemWritableFileStream` là một phần của API File System Access, cho phép các ứng dụng web truy cập và thao tác với tệp tin trên máy tính của người dùng. API này rất hữu ích cho các ứng dụng cần lưu trữ và quản lý tệp tin, như trình soạn thảo văn bản hoặc ứng dụng vẽ.

### Mục Đích
Mục đích của `FileSystemWritableFileStream` là cung cấp một cách đơn giản và an toàn để ghi dữ liệu vào tệp tin, với khả năng hỗ trợ viết dữ liệu không đồng bộ.

### Cách Sử Dụng
Để sử dụng `FileSystemWritableFileStream`, trước tiên bạn cần lấy một đối tượng `FileSystemFileHandle` thông qua API File System Access. Sau đó, bạn có thể gọi phương thức `createWritable()` để tạo một `FileSystemWritableFileStream`.

```javascript
async function writeFile() {
    // Lấy file handle từ dialog chọn file
    const [fileHandle] = await window.showOpenFilePicker();
    
    // Tạo writable stream
    const writableStream = await fileHandle.createWritable();

    // Ghi dữ liệu vào tệp
    await writableStream.write('Hello, World!');

    // Đóng stream sau khi ghi xong
    await writableStream.close();
}
```

## Ví Dụ
### Ghi Dữ Liệu Vào Tệp
```javascript
async function saveTextToFile() {
    const fileHandle = await window.showSaveFilePicker({
        suggestedName: 'example.txt',
        types: [{
            description: 'Text Files',
            accept: {'text/plain': ['.txt']},
        }],
    });

    const writableStream = await fileHandle.createWritable();
    await writableStream.write('Nội dung tệp tin!');
    await writableStream.close();
}
```

### Ghi Dữ Liệu Vào Tệp Hình Ảnh
```javascript
async function saveImageToFile(blob) {
    const fileHandle = await window.showSaveFilePicker({
        suggestedName: 'image.png',
        types: [{
            description: 'PNG Images',
            accept: {'image/png': ['.png']},
        }],
    });

    const writableStream = await fileHandle.createWritable();
    await writableStream.write(blob);
    await writableStream.close();
}
```

## Giải Thích
### Những Điều Cần Lưu Ý
- **Quyền Truy Cập**: Người dùng cần cho phép quyền truy cập tệp tin, vì vậy hãy chắc chắn rằng bạn xử lý tình huống từ chối quyền truy cập một cách hợp lý.
- **Đồng Bộ Hóa**: Tất cả các hành động ghi cần được thực hiện không đồng bộ, do đó hãy sử dụng `async/await` hoặc `Promise` để tránh tình trạng rối loạn.
- **Đóng Stream**: Luôn nhớ đóng stream sau khi hoàn tất để giải phóng tài nguyên và đảm bảo dữ liệu được ghi đúng cách.

## Tóm Tắt Một Dòng
`FileSystemWritableFileStream` trong JavaScript cho phép ghi dữ liệu vào tệp tin trên hệ thống tệp của trình duyệt một cách an toàn và hiệu quả.