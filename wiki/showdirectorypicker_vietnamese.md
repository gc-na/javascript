<!--
Meta Description: # showDirectoryPicker: Hướng Dẫn Sử Dụng và Ví Dụ Cụ Thể trong JavaScript ## Tóm Tắt `showDirectoryPicker` là một phương thức trong JavaScript cho phé...
Meta Keywords: một, showdirectorypicker, dụng, trong, mục
-->

# showDirectoryPicker: Hướng Dẫn Sử Dụng và Ví Dụ Cụ Thể trong JavaScript

## Tóm Tắt
`showDirectoryPicker` là một phương thức trong JavaScript cho phép người dùng chọn một thư mục từ hệ thống tệp của họ. Tính năng này giúp các ứng dụng web tương tác với tệp tin một cách dễ dàng hơn.

## Tài Liệu
### Mục Đích
`showDirectoryPicker` được sử dụng để mở hộp thoại cho phép người dùng chọn một thư mục. Tính năng này rất hữu ích cho các ứng dụng cần thao tác với nhiều tệp tin trong cùng một thư mục.

### Cách Sử Dụng
Để sử dụng `showDirectoryPicker`, bạn cần gọi phương thức này trên một đối tượng `window`, và nó sẽ trả về một `Promise` chứa `FileSystemDirectoryHandle`. 

### Cú Pháp
```javascript
async function pickDirectory() {
    const dirHandle = await window.showDirectoryPicker();
    // Thao tác với thư mục đã chọn
}
```

### Chi Tiết
- **Trả về**: Một `Promise` sẽ được giải quyết thành `FileSystemDirectoryHandle`.
- **Điều kiện**: Phương thức này chỉ có thể được gọi trong một ngữ cảnh tương tác với người dùng, như một sự kiện `click`.

## Ví Dụ
### Ví Dụ Cơ Bản
```javascript
async function pickDirectory() {
    try {
        const dirHandle = await window.showDirectoryPicker();
        console.log("Thư mục đã chọn:", dirHandle.name);
    } catch (error) {
        console.error("Đã xảy ra lỗi:", error);
    }
}
```

### Ví Dụ Với Thao Tác Tệp
```javascript
async function pickAndReadFiles() {
    const dirHandle = await window.showDirectoryPicker();
    for await (const entry of dirHandle.values()) {
        console.log("Tệp trong thư mục:", entry.name);
    }
}
```

## Giải Thích
### Những Lưu Ý Thường Gặp
- **Quyền Truy Cập**: Người dùng cần cấp quyền cho ứng dụng web để truy cập vào hệ thống tệp.
- **Ngữ Cảnh Gọi**: Nếu không gọi trong một sự kiện tương tác, phương thức sẽ thất bại.
- **Hỗ Trợ Trình Duyệt**: Tính năng này không được hỗ trợ trên tất cả các trình duyệt, vì vậy cần kiểm tra khả năng tương thích.

### Cách Giải Quyết Lỗi
Nếu bạn gặp lỗi khi gọi `showDirectoryPicker`, hãy chắc chắn rằng bạn đang chạy mã trong một ngữ cảnh tương tác (như sự kiện `click`). Đồng thời, kiểm tra khả năng tương thích trình duyệt.

## Tóm Tắt Một Câu
`showDirectoryPicker` trong JavaScript cho phép người dùng chọn một thư mục từ hệ thống tệp, mang lại sự tiện lợi cho các ứng dụng web.