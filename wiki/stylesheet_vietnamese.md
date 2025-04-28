<!--
Meta Description: # StyleSheet trong JavaScript: Hướng Dẫn Chi Tiết ## Tóm tắt StyleSheet trong JavaScript cho phép lập trình viên thao tác với các quy tắc CSS, điều ch...
Meta Keywords: quy, tắc, stylesheet, các, một
-->

# StyleSheet trong JavaScript: Hướng Dẫn Chi Tiết

## Tóm tắt
StyleSheet trong JavaScript cho phép lập trình viên thao tác với các quy tắc CSS, điều chỉnh giao diện của trang web một cách linh hoạt và động.

## Tài liệu
### Mục đích
StyleSheet là một phần quan trọng trong việc quản lý và áp dụng các kiểu dáng cho các phần tử trên một trang web. Thông qua JavaScript, bạn có thể thêm, sửa đổi hoặc xóa các quy tắc CSS trong tài liệu HTML.

### Cách sử dụng
Để làm việc với StyleSheet trong JavaScript, bạn có thể sử dụng thuộc tính `document.styleSheets`. Đây là một danh sách chứa tất cả các StyleSheet hiện có trong tài liệu. Bạn có thể truy cập và thay đổi các quy tắc bằng cách sử dụng các phương thức như `insertRule()` và `deleteRule()`.

#### Cú pháp cơ bản
```javascript
// Lấy danh sách các StyleSheet
const styleSheets = document.styleSheets;

// Thêm một quy tắc mới
styleSheets[0].insertRule('body { background-color: blue; }', styleSheets[0].cssRules.length);

// Xóa một quy tắc
styleSheets[0].deleteRule(0);
```

## Ví dụ
### Ví dụ 1: Thêm quy tắc CSS mới
```javascript
// Thêm một quy tắc cho tất cả các đoạn văn
document.styleSheets[0].insertRule('p { color: red; }', document.styleSheets[0].cssRules.length);
```

### Ví dụ 2: Xóa quy tắc CSS
```javascript
// Xóa quy tắc đầu tiên trong StyleSheet đầu tiên
document.styleSheets[0].deleteRule(0);
```

## Giải thích
### Những điều cần lưu ý
- **Trình duyệt hỗ trợ**: Không phải tất cả trình duyệt đều hỗ trợ đầy đủ các phương thức liên quan đến StyleSheet. Hãy kiểm tra tính tương thích trước khi sử dụng.
- **Lỗi khi thêm quy tắc**: Khi thêm quy tắc, đảm bảo rằng cú pháp CSS là chính xác. Nếu không, trình duyệt sẽ ném ra lỗi và quy tắc sẽ không được áp dụng.

### Một số điểm cần lưu ý
- Quy tắc CSS được thêm vào sẽ có tác động ngay lập tức đến giao diện người dùng nếu không có lỗi.
- Bạn có thể thao tác với nhiều StyleSheet trong tài liệu, vì vậy hãy chắc chắn chọn đúng StyleSheet mà bạn muốn làm việc.

## Tóm tắt một dòng
StyleSheet trong JavaScript cho phép bạn thêm, sửa đổi và xóa các quy tắc CSS để điều chỉnh giao diện của trang web một cách linh hoạt.