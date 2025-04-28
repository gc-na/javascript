<!--
Meta Description: # Quy Tắc Bắt Đầu CSS Trong JavaScript: CSSStartingStyleRule ## Tóm Tắt `CSSStartingStyleRule` là một đối tượng trong JavaScript, thuộc về API CSSOM, ...
Meta Keywords: quy, tắc, css, cssstartingstylerule, một
-->

# Quy Tắc Bắt Đầu CSS Trong JavaScript: CSSStartingStyleRule

## Tóm Tắt
`CSSStartingStyleRule` là một đối tượng trong JavaScript, thuộc về API CSSOM, cho phép lập trình viên truy cập và thao tác với các quy tắc kiểu CSS trong tài liệu HTML. Đối tượng này hữu ích trong việc tạo ra và quản lý các quy tắc CSS động.

## Tài Liệu
### Mục Đích
`CSSStartingStyleRule` được sử dụng để đại diện cho một quy tắc CSS cụ thể trong một tập hợp quy tắc. Nó giúp lập trình viên dễ dàng truy cập và điều chỉnh các thuộc tính của quy tắc đó thông qua JavaScript.

### Cách Sử Dụng
Để sử dụng `CSSStartingStyleRule`, bạn thường cần phải truy cập một đối tượng CSSStyleSheet và sau đó lấy quy tắc từ đó. Dưới đây là cú pháp cơ bản để truy cập và thay đổi quy tắc CSS:

```javascript
const stylesheet = document.styleSheets[0]; // Lấy stylesheet đầu tiên
const rule = stylesheet.cssRules[0]; // Lấy quy tắc đầu tiên
if (rule instanceof CSSStartingStyleRule) {
    // Thao tác với quy tắc
}
```

### Chi Tiết
- `CSSStartingStyleRule` là một phần của giao diện `CSSRule`, cho phép bạn làm việc với các thuộc tính như `selectorText`, `style`, và nhiều thuộc tính khác liên quan đến quy tắc CSS.
- Bạn có thể sử dụng các phương thức như `insertRule()` và `deleteRule()` để quản lý quy tắc trong bảng kiểu.

## Ví Dụ
### Ví Dụ 1: Thêm Quy Tắc CSS Mới
```javascript
const stylesheet = document.styleSheets[0];
stylesheet.insertRule('body { background-color: blue; }', stylesheet.cssRules.length);
```

### Ví Dụ 2: Thay Đổi Quy Tắc CSS
```javascript
const stylesheet = document.styleSheets[0];
const rule = stylesheet.cssRules[0]; // Giả sử quy tắc đầu tiên là 'h1 { color: red; }'
if (rule instanceof CSSStartingStyleRule) {
    rule.style.color = 'green'; // Thay đổi màu sắc thành xanh
}
```

## Giải Thích
- **Cảnh báo Thường Gặp**: Một số trình duyệt có thể không hỗ trợ hoàn toàn API CSSOM, vì vậy cần đảm bảo kiểm tra tính tương thích trước khi sử dụng.
- **Hiệu Suất**: Thao tác trực tiếp trên các quy tắc CSS có thể ảnh hưởng đến hiệu suất của trang, đặc biệt nếu có nhiều quy tắc hoặc thao tác liên tục.
- **Quy Tắc Không Hợp Lệ**: Nếu bạn cố gắng truy cập một quy tắc không phải là `CSSStartingStyleRule`, hãy chắc chắn rằng bạn kiểm tra kiểu dữ liệu để tránh lỗi.

## Tóm Tắt Một Dòng
`CSSStartingStyleRule` cho phép lập trình viên truy cập và thao tác với các quy tắc CSS trong tài liệu HTML thông qua JavaScript.