<!--
Meta Description: # FileSystemHandle trong JavaScript: Quản lý Tập tin và Thư mục ## Tóm Tắt `FileSystemHandle` là một phần của API File System Access trong JavaScript,...
Meta Keywords: tập, tin, await, một, các
-->

# FileSystemHandle trong JavaScript: Quản lý Tập tin và Thư mục

## Tóm Tắt
`FileSystemHandle` là một phần của API File System Access trong JavaScript, cho phép người dùng truy cập và quản lý các tập tin và thư mục trên hệ thống tệp của họ một cách an toàn và thuận tiện.

## Tài Liệu
`FileSystemHandle` là một giao diện trong JavaScript được thiết kế để làm việc với các tập tin và thư mục trên hệ thống tệp của người dùng. API này cho phép các ứng dụng web truy cập, đọc, ghi và quản lý tập tin mà không cần phải sử dụng các phương thức phức tạp hơn như tải lên và tải xuống.

### Mục Đích
Mục đích chính của `FileSystemHandle` là cung cấp một cách an toàn để các ứng dụng web tương tác với hệ thống tệp cục bộ, cho phép người dùng chọn tập tin và thư mục mà họ muốn làm việc mà không cần phải rời khỏi trình duyệt.

### Cách Sử Dụng
Để sử dụng `FileSystemHandle`, người dùng cần phải yêu cầu quyền truy cập vào hệ thống tệp của họ thông qua API File System Access. Dưới đây là một số bước cơ bản để thực hiện:

1. **Yêu cầu quyền truy cập** bằng cách sử dụng `window.showOpenFilePicker()` hoặc `window.showDirectoryPicker()`.
2. **Làm việc với các đối tượng `FileSystemHandle`** để đọc hoặc ghi dữ liệu.

```javascript
async function openFile() {
    const [fileHandle] = await window.showOpenFilePicker();
    const file = await fileHandle.getFile();
    const contents = await file.text();
    console.log(contents);
}
```

## Ví Dụ
### Ví dụ 1: Mở và Đọc Tập Tin
```javascript
async function readFile() {
    const [fileHandle] = await window.showOpenFilePicker();
    const file = await fileHandle.getFile();
    const text = await file.text();
    console.log(text);
}

readFile();
```

### Ví dụ 2: Lưu Tập Tin
```javascript
async function saveFile() {
    const fileHandle = await window.showSaveFilePicker();
    const writable = await fileHandle.createWritable();
    await writable.write('Hello, World!');
    await writable.close();
}

saveFile();
```

## Giải Thích
Khi làm việc với `FileSystemHandle`, có một số điều cần lưu ý:

- **Quyền Truy Cập**: Người dùng phải cấp quyền truy cập cho trình duyệt để có thể sử dụng API này. Điều này có nghĩa là người dùng phải chọn tập tin hoặc thư mục mỗi lần.
- **Không Hỗ Trợ Trên Tất Cả Các Trình Duyệt**: API File System Access hiện tại không được hỗ trợ trên tất cả các trình duyệt, vì vậy cần kiểm tra tính khả dụng trước khi sử dụng.
- **Quản Lý Lỗi**: Hãy chắc chắn xử lý các lỗi có thể xảy ra trong quá trình truy cập và làm việc với tập tin.

## Tóm Tắt Một Dòng
`FileSystemHandle` là một giao diện trong JavaScript cho phép truy cập và quản lý tập tin và thư mục trên hệ thống tệp của người dùng một cách an toàn và dễ dàng.