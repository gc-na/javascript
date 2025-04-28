<!--
Meta Description: # DocumentType trong JavaScript: Tìm Hiểu về Đối Tượng DocumentType ## Tóm tắt DocumentType là một đối tượng trong JavaScript đại diện cho phần khai b...
Meta Keywords: documenttype, doctype, tài, liệu, document
-->

# DocumentType trong JavaScript: Tìm Hiểu về Đối Tượng DocumentType

## Tóm tắt
DocumentType là một đối tượng trong JavaScript đại diện cho phần khai báo loại tài liệu (doctype) của một trang web, giúp trình duyệt hiểu cách để xử lý và hiển thị nội dung HTML.

## Tài liệu
### Mục đích
DocumentType là một phần quan trọng trong cấu trúc HTML, dùng để chỉ rõ phiên bản HTML mà tài liệu đang sử dụng. Trong JavaScript, đối tượng DocumentType cho phép lập trình viên truy cập và thay đổi thông tin này.

### Cách sử dụng
Đối tượng DocumentType có thể được truy cập thông qua thuộc tính `doctype` của đối tượng `document`. Điều này cho phép bạn kiểm tra hoặc thay đổi loại tài liệu cho một trang web.

**Cú pháp:**
```javascript
let doctype = document.doctype;
```

### Chi tiết
- **Trả về:** Đối tượng DocumentType hoặc `null` nếu không có loại tài liệu nào.
- **Thuộc tính:** 
  - `name`: Tên của loại tài liệu.
  - `publicId`: ID công khai của loại tài liệu.
  - `systemId`: ID hệ thống của loại tài liệu.

## Ví dụ
### Ví dụ cơ bản
```javascript
// Lấy đối tượng DocumentType
let doctype = document.doctype;

// Kiểm tra và hiển thị thông tin về DocumentType
if (doctype) {
    console.log("Tên: " + doctype.name);
    console.log("Public ID: " + doctype.publicId);
    console.log("System ID: " + doctype.systemId);
} else {
    console.log("Không có DocumentType.");
}
```

### Ví dụ thay đổi DocumentType
```javascript
// Thay đổi DocumentType (không trực tiếp, chỉ có thể thông qua HTML)
document.open();
document.write('<!DOCTYPE html>');
document.close();
```

## Giải thích
Khi làm việc với DocumentType, có một số điều cần lưu ý:
- DocumentType không thể được thay đổi trực tiếp thông qua JavaScript sau khi tài liệu đã được tải. Bạn cần phải sử dụng `document.open()`, `document.write()`, và `document.close()` để thay thế toàn bộ nội dung, bao gồm cả DocumentType.
- Nếu không có DocumentType, một số trình duyệt có thể chuyển sang chế độ "quirks mode", có thể dẫn đến việc hiển thị không chính xác.

## Tóm tắt một dòng
DocumentType trong JavaScript cho phép truy cập và kiểm soát phần khai báo loại tài liệu của một trang web, ảnh hưởng đến cách trình duyệt hiển thị nội dung.