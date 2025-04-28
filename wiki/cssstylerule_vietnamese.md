<!--
Meta Description: # CSSStyleRule trong JavaScript: Hướng Dẫn Toàn Diện ## Tóm tắt `CSSStyleRule` là một giao diện trong JavaScript cho phép lập trình viên truy xuất và ...
Meta Keywords: quy, tắc, css, một, các
-->

# CSSStyleRule trong JavaScript: Hướng Dẫn Toàn Diện

## Tóm tắt
`CSSStyleRule` là một giao diện trong JavaScript cho phép lập trình viên truy xuất và thao tác với các quy tắc CSS trong tài liệu. Nó giúp quản lý và thay đổi các thuộc tính CSS một cách linh hoạt và dễ dàng.

## Tài liệu
### Mục đích
`CSSStyleRule` đại diện cho một quy tắc CSS trong một stylesheet. Nó cho phép lập trình viên truy cập và điều chỉnh các thuộc tính của quy tắc CSS, từ đó giúp tương tác với giao diện người dùng một cách hiệu quả.

### Cách sử dụng
`CSSStyleRule` thường được sử dụng trong bối cảnh của đối tượng `CSSRule`. Để lấy được một quy tắc CSS cụ thể, bạn cần truy cập vào stylesheet và sau đó vào danh sách các quy tắc của nó.

### Chi tiết
- **Thuộc tính**:
  - `selectorText`: Trả về chuỗi chứa bộ chọn CSS của quy tắc.
  - `style`: Trả về đối tượng `CSSStyleDeclaration` chứa tất cả các thuộc tính CSS mà quy tắc áp dụng.
  
- **Phương thức**:
  - `deleteProperty(property)`: Xóa thuộc tính CSS cụ thể khỏi quy tắc.
  - `setProperty(property, value, priority)`: Thiết lập thuộc tính CSS với giá trị và độ ưu tiên (nếu cần).

## Ví dụ
### Ví dụ cơ bản
```javascript
// Lấy stylesheet đầu tiên trong tài liệu
let stylesheet = document.styleSheets[0];

// Lấy quy tắc đầu tiên trong stylesheet
let rule = stylesheet.cssRules[0];

// Hiển thị bộ chọn quy tắc
console.log(rule.selectorText); // '.my-class'

// Thay đổi thuộc tính màu sắc của quy tắc
rule.style.setProperty('color', 'red');

// Xóa thuộc tính nền của quy tắc
rule.style.deleteProperty('background-color');
```

### Ví dụ về việc thêm quy tắc mới
```javascript
// Tạo một quy tắc CSS mới
let newRule = '.new-class { color: blue; }';

// Thêm quy tắc mới vào stylesheet
stylesheet.insertRule(newRule, stylesheet.cssRules.length);
```

## Giải thích
- **Những cạm bẫy thường gặp**: Một số nhà phát triển có thể không nhận ra rằng không phải tất cả các stylesheet đều có thể được truy cập và thay đổi, đặc biệt là khi chúng được tải từ các nguồn khác như CDN hoặc có chính sách CORS nghiêm ngặt.
- **Điểm cần lưu ý**: Khi làm việc với các quy tắc CSS, hãy chắc chắn rằng bạn kiểm tra sự tồn tại của quy tắc trước khi thao tác với nó để tránh lỗi.

## Tóm tắt một dòng
`CSSStyleRule` là một giao diện JavaScript cho phép thao tác với các quy tắc CSS, cung cấp khả năng truy xuất và chỉnh sửa các thuộc tính CSS một cách linh hoạt.