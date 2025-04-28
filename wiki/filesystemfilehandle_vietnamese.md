<!--
Meta Description: # FileSystemFileHandle trong JavaScript: Hướng Dẫn Chi Tiết ## Tóm Tắt `FileSystemFileHandle` là một interface trong JavaScript cho phép truy cập và t...
Meta Keywords: tệp, filesystemfilehandle, các, người, dùng
-->

# FileSystemFileHandle trong JavaScript: Hướng Dẫn Chi Tiết

## Tóm Tắt
`FileSystemFileHandle` là một interface trong JavaScript cho phép truy cập và thao tác với các tập tin trên hệ thống tệp của người dùng thông qua API File System Access. Nó giúp các nhà phát triển dễ dàng làm việc với các tệp mà không cần phải sử dụng các phương thức truyền thống như `FileReader` hay `XMLHttpRequest`.

## Tài liệu
### Mục đích
`FileSystemFileHandle` được thiết kế để cung cấp một cách an toàn và hiệu quả cho việc đọc, ghi và quản lý các tệp trên hệ thống tệp của người dùng. Thông qua API này, người dùng có thể chọn và thao tác với các tệp mà họ muốn, mang lại trải nghiệm tương tác hơn cho ứng dụng web.

### Cách Sử Dụng
Để sử dụng `FileSystemFileHandle`, bạn cần thực hiện các bước sau:
1. Yêu cầu quyền truy cập đến tệp thông qua `showOpenFilePicker()`.
2. Lấy `FileSystemFileHandle` từ tệp đã chọn.
3. Sử dụng các phương thức của `FileSystemFileHandle` để đọc hoặc ghi dữ liệu.

### Chi Tiết
- **Phương thức chính**:
  - `getFile()`: Lấy đối tượng `File` tương ứng với `FileSystemFileHandle`.
  - `createWritable()`: Tạo một đối tượng `FileSystemWritableFileHandle` để ghi dữ liệu vào tệp.

- **Quyền truy cập**: Để có thể sử dụng `FileSystemFileHandle`, trình duyệt cần được cấp quyền truy cập đến tệp. Điều này thường được thực hiện thông qua giao diện người dùng.

## Ví Dụ
### Ví dụ 1: Mở và Đọc Tệp
```javascript
async function openAndReadFile() {
    // Cho phép người dùng chọn tệp
    const [fileHandle] = await window.showOpenFilePicker();
    // Lấy đối tượng File
    const file = await fileHandle.getFile();
    // Đọc nội dung tệp
    const text = await file.text();
    console.log(text);
}
```

### Ví dụ 2: Ghi Dữ Liệu vào Tệp
```javascript
async function saveFile() {
    const fileHandle = await window.showSaveFilePicker();
    const writable = await fileHandle.createWritable();
    await writable.write('Nội dung mới cho tệp.');
    await writable.close();
}
```

## Giải Thích
### Những Lưu Ý Chung
- **Trình duyệt hỗ trợ**: `FileSystemFileHandle` chỉ được hỗ trợ trên một số trình duyệt nhất định, vì vậy hãy kiểm tra khả năng tương thích.
- **Quyền truy cập**: Tất cả các thao tác với tệp yêu cầu người dùng phải tương tác với giao diện, không thể tự động hóa hoàn toàn.
- **Nguyên tắc bảo mật**: API này tuân thủ nguyên tắc bảo mật, giúp bảo vệ thông tin cá nhân của người dùng.

## Tóm Tắt Một Dòng
`FileSystemFileHandle` trong JavaScript cho phép truy cập và thao tác an toàn với các tệp trên hệ thống tệp của người dùng thông qua API File System Access.