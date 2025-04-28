<!--
Meta Description: # StaticRange trong JavaScript: Tìm Hiểu và Ứng Dụng ## Tóm Tắt `StaticRange` là một đối tượng trong JavaScript được sử dụng để đại diện cho một khoản...
Meta Keywords: staticrange, một, chọn, selection, khoảng
-->

# StaticRange trong JavaScript: Tìm Hiểu và Ứng Dụng

## Tóm Tắt
`StaticRange` là một đối tượng trong JavaScript được sử dụng để đại diện cho một khoảng chọn tĩnh trong tài liệu, cho phép bạn làm việc với các đoạn văn bản hoặc phần tử DOM mà không bị ảnh hưởng bởi sự thay đổi trong tài liệu.

## Tài Liệu
`StaticRange` là một phần của API DOM Selection, được giới thiệu để cung cấp một cách tiếp cận tiện lợi và hiệu quả hơn khi làm việc với các đoạn văn bản đã chọn. Đối tượng `StaticRange` cho phép bạn tạo và truy cập các thông tin về một khoảng chọn mà không thay đổi khi tài liệu bị thay đổi.

### Mục Đích
- Để làm việc với các khoảng chọn văn bản mà không bị thay đổi bởi các tương tác khác trong tài liệu.
- Để dễ dàng xác định các phần tử DOM liên quan đến một khoảng chọn văn bản cụ thể.

### Cách Sử Dụng
Để tạo một đối tượng `StaticRange`, bạn cần sử dụng hàm khởi tạo `StaticRange`, với hai tham số chính:
- `startContainer`: Phần tử DOM nơi bắt đầu khoảng chọn.
- `startOffset`: Vị trí bắt đầu trong phần tử.
- `endContainer`: Phần tử DOM nơi kết thúc khoảng chọn.
- `endOffset`: Vị trí kết thúc trong phần tử.

Cú pháp:
```javascript
let staticRange = new StaticRange({
    startContainer: /* phần tử bắt đầu */,
    startOffset: /* offset bắt đầu */,
    endContainer: /* phần tử kết thúc */,
    endOffset: /* offset kết thúc */
});
```

## Ví Dụ
### Ví Dụ 1: Tạo StaticRange từ một khoảng chọn
```javascript
let selection = window.getSelection();
let staticRange = new StaticRange({
    startContainer: selection.anchorNode,
    startOffset: selection.anchorOffset,
    endContainer: selection.focusNode,
    endOffset: selection.focusOffset
});
console.log(staticRange); // In thông tin của StaticRange
```

### Ví Dụ 2: Kiểm tra các thuộc tính của StaticRange
```javascript
let selection = window.getSelection();
let staticRange = new StaticRange({
    startContainer: selection.anchorNode,
    startOffset: selection.anchorOffset,
    endContainer: selection.focusNode,
    endOffset: selection.focusOffset
});

console.log(staticRange.startContainer);
console.log(staticRange.endContainer);
console.log(staticRange.startOffset);
console.log(staticRange.endOffset);
```

## Giải Thích
Một số điểm cần lưu ý khi làm việc với `StaticRange`:
- `StaticRange` không tự động cập nhật khi nội dung tài liệu thay đổi, do đó, bạn cần tạo một `StaticRange` mới nếu nội dung thay đổi ảnh hưởng đến khoảng chọn.
- `StaticRange` có thể không hoạt động như mong đợi nếu không có một khoảng chọn hợp lệ được cung cấp.

## Tóm Tắt Một Dòng
`StaticRange` trong JavaScript là một công cụ mạnh mẽ cho phép đại diện và làm việc với các khoảng chọn văn bản tĩnh trong tài liệu mà không bị ảnh hưởng bởi sự thay đổi nội dung.