<!--
Meta Description: # CSSStyleSheet trong JavaScript: Hướng Dẫn Chi Tiết ## Tóm tắt `CSSStyleSheet` là một đối tượng trong JavaScript cho phép lập trình viên tương tác vớ...
Meta Keywords: quy, tắc, css, stylesheet, các
-->

# CSSStyleSheet trong JavaScript: Hướng Dẫn Chi Tiết

## Tóm tắt
`CSSStyleSheet` là một đối tượng trong JavaScript cho phép lập trình viên tương tác với các stylesheet trong tài liệu HTML, cho phép thao tác và thay đổi các quy tắc CSS một cách linh hoạt.

## Tài liệu
### Mục đích
`CSSStyleSheet` đại diện cho một stylesheet trong tài liệu HTML. Nó cho phép bạn truy cập và chỉnh sửa các quy tắc CSS mà không cần phải thay đổi các tệp CSS bên ngoài.

### Cách sử dụng
Để sử dụng `CSSStyleSheet`, bạn có thể truy cập nó thông qua thuộc tính `styleSheets` của đối tượng `document`. Mỗi stylesheet có thể chứa nhiều quy tắc CSS, mà bạn có thể thao tác thông qua thuộc tính `cssRules`.

#### Cú pháp
```javascript
let sheet = document.styleSheets[index];
```

- `index`: chỉ số của stylesheet mà bạn muốn truy cập (bắt đầu từ 0).

### Chi tiết
- `CSSStyleSheet` cung cấp các thuộc tính và phương thức như:
  - `insertRule(rule, index)`: Thêm một quy tắc CSS mới vào vị trí chỉ định.
  - `deleteRule(index)`: Xóa quy tắc CSS tại vị trí chỉ định.
  - `cssRules`: Trả về danh sách tất cả các quy tắc CSS trong stylesheet.

## Ví dụ
### Thêm quy tắc CSS mới
```javascript
let stylesheet = document.styleSheets[0];
stylesheet.insertRule('body { background-color: lightblue; }', stylesheet.cssRules.length);
```

### Xóa quy tắc CSS
```javascript
let stylesheet = document.styleSheets[0];
stylesheet.deleteRule(0); // Xóa quy tắc đầu tiên
```

### Lấy danh sách các quy tắc CSS
```javascript
let stylesheet = document.styleSheets[0];
console.log(stylesheet.cssRules);
```

## Giải thích
- **Điểm cần lưu ý**: Một số trình duyệt có thể không hỗ trợ đầy đủ các phương thức của `CSSStyleSheet`, vì vậy bạn nên kiểm tra tính tương thích trước khi sử dụng.
- **Quy tắc CSS**: Khi thêm quy tắc, hãy chắc chắn rằng cú pháp CSS đúng; nếu không, sẽ xảy ra lỗi.
- **Thay đổi động**: Các thay đổi được thực hiện thông qua `CSSStyleSheet` sẽ áp dụng ngay lập tức mà không cần tải lại trang.

## Tóm tắt một dòng
`CSSStyleSheet` trong JavaScript cho phép bạn thao tác và quản lý các quy tắc CSS trong tài liệu HTML một cách linh hoạt và hiệu quả.