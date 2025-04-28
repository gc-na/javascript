<!--
Meta Description: # CSSPageRule trong JavaScript: Tìm hiểu và Ứng dụng ## Tóm tắt CSSPageRule là một đối tượng trong JavaScript, cho phép lập trình viên thao tác với cá...
Meta Keywords: quy, tắc, các, stylesheet, css
-->

# CSSPageRule trong JavaScript: Tìm hiểu và Ứng dụng

## Tóm tắt
CSSPageRule là một đối tượng trong JavaScript, cho phép lập trình viên thao tác với các quy tắc CSS trong tài liệu kiểu. Nó giúp quản lý các quy tắc CSS cho các trang in, cho phép thay đổi cách mà nội dung được hiển thị khi in.

## Tài liệu
### Mục đích
CSSPageRule được sử dụng để truy cập và điều chỉnh các quy tắc CSS liên quan đến các trang in. Bằng cách sử dụng đối tượng này, bạn có thể thay đổi các thuộc tính của trang in một cách linh hoạt và dễ dàng.

### Cách sử dụng
Để sử dụng CSSPageRule, bạn cần phải truy cập nó thông qua đối tượng CSSStyleSheet. Đầu tiên, bạn sẽ cần tạo một quy tắc CSS cho trang in, sau đó sử dụng CSSPageRule để thay đổi hoặc xóa quy tắc đó.

### Chi tiết
- **Thuộc tính**: 
  - `selectorText`: Lấy hoặc thiết lập văn bản selector của quy tắc.
  - `style`: Trả về một đối tượng CSSStyleDeclaration chứa các thuộc tính CSS.
- **Phương thức**: 
  - `deleteRule()`: Xóa quy tắc hiện tại khỏi stylesheet.

## Ví dụ
### Ví dụ cơ bản về CSSPageRule

```javascript
// Lấy stylesheet đầu tiên trong tài liệu
let stylesheet = document.styleSheets[0];

// Thêm một quy tắc CSS cho trang in
stylesheet.insertRule('@page { margin: 2cm; }', stylesheet.cssRules.length);

// Lấy quy tắc @page
let pageRule = stylesheet.cssRules[stylesheet.cssRules.length - 1];

// Hiển thị selectorText
console.log(pageRule.selectorText); // @page

// Thay đổi thuộc tính margin
pageRule.style.margin = '1cm';
```

### Xóa quy tắc CSS
```javascript
// Xóa quy tắc @page đã thêm
stylesheet.deleteRule(stylesheet.cssRules.length - 1);
```

## Giải thích
### Các điểm cần lưu ý
- **Hỗ trợ trình duyệt**: CSSPageRule có thể không được hỗ trợ trong tất cả các trình duyệt. Hãy kiểm tra tính tương thích trước khi sử dụng.
- **Thao tác trên stylesheets**: Nếu bạn cố gắng truy cập hoặc thay đổi quy tắc CSS trong một stylesheet từ một miền khác, bạn có thể gặp phải lỗi về chính sách cùng nguồn gốc (CORS).
- **Thứ tự quy tắc**: Thứ tự của quy tắc trong stylesheet có thể ảnh hưởng đến cách mà các quy tắc CSS được áp dụng.

## Tóm tắt một dòng
CSSPageRule trong JavaScript cho phép bạn truy cập và điều chỉnh các quy tắc CSS cho trang in một cách linh hoạt và hiệu quả.