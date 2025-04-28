<!--
Meta Description: # CSSFontFaceRule trong JavaScript: Hướng dẫn chi tiết ## Tóm tắt CSSFontFaceRule là một đối tượng trong JavaScript cho phép lập trình viên truy cập v...
Meta Keywords: chữ, phông, quy, tắc, font
-->

# CSSFontFaceRule trong JavaScript: Hướng dẫn chi tiết

## Tóm tắt
CSSFontFaceRule là một đối tượng trong JavaScript cho phép lập trình viên truy cập và thao tác với quy tắc `@font-face` trong CSS. Điều này giúp quản lý và sử dụng các phông chữ tùy chỉnh trong các ứng dụng web một cách hiệu quả.

## Tài liệu
### Mục đích
CSSFontFaceRule cho phép bạn tạo và chỉnh sửa các quy tắc phông chữ tùy chỉnh, giúp cải thiện trải nghiệm người dùng bằng cách áp dụng các kiểu chữ độc đáo cho trang web.

### Cách sử dụng
Để sử dụng CSSFontFaceRule, bạn cần truy cập từ đối tượng `CSSStyleSheet`. Bạn có thể tạo một quy tắc phông chữ mới và thêm nó vào stylesheet bằng phương pháp `insertRule()`.

#### Cú pháp
```javascript
let sheet = document.styleSheets[0];
let rule = sheet.insertRule("@font-face { font-family: 'MyFont'; src: url('myfont.woff2'); }", sheet.cssRules.length);
```

### Chi tiết
- `font-family`: Tên của phông chữ mà bạn muốn định nghĩa.
- `src`: Đường dẫn tới tệp phông chữ.
- Bạn có thể truy cập các thuộc tính của CSSFontFaceRule như `style`, `fontFamily`, và `src` để thay đổi quy tắc phông chữ đã định nghĩa.

## Ví dụ
### Ví dụ 1: Thêm một phông chữ tùy chỉnh
```javascript
let sheet = document.styleSheets[0];
sheet.insertRule("@font-face { font-family: 'MyCustomFont'; src: url('mycustomfont.woff'); }", sheet.cssRules.length);
```

### Ví dụ 2: Thay đổi phông chữ đã có
```javascript
let sheet = document.styleSheets[0];
let rule = sheet.cssRules[0]; // Giả sử quy tắc đầu tiên là quy tắc @font-face
rule.style.fontFamily = "'NewFontName'";
```

## Giải thích
- **Cảnh báo**: Nếu bạn thêm quy tắc phông chữ nhưng không có tệp phông chữ tương ứng, trình duyệt sẽ không thể tải phông chữ đó.
- **Hỗ trợ trình duyệt**: Đảm bảo rằng các tệp phông chữ được cung cấp ở định dạng mà tất cả các trình duyệt chính hỗ trợ, chẳng hạn như WOFF hoặc WOFF2.
- **Quy tắc**: Các quy tắc `@font-face` nên được định nghĩa ở đầu CSS để đảm bảo rằng chúng có sẵn khi trang được tải.

## Tóm tắt một dòng
CSSFontFaceRule trong JavaScript cho phép bạn quản lý và thao tác với quy tắc phông chữ tùy chỉnh, nâng cao tính năng và thiết kế của trang web.