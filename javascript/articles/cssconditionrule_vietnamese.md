<!--
Meta Description: # CSSConditionRule trong JavaScript: Hướng dẫn đầy đủ ## Tóm tắt CSSConditionRule là một đối tượng trong JavaScript cho phép bạn làm việc với các quy ...
Meta Keywords: quy, tắc, điều, các, kiện
-->

# CSSConditionRule trong JavaScript: Hướng dẫn đầy đủ

## Tóm tắt
CSSConditionRule là một đối tượng trong JavaScript cho phép bạn làm việc với các quy tắc điều kiện trong CSS, như `@media` và `@supports`. Nó cung cấp một cách để truy cập và sửa đổi các quy tắc CSS dựa trên điều kiện.

## Tài liệu
### Mục đích
CSSConditionRule được sử dụng để quản lý các quy tắc CSS có điều kiện, cho phép bạn tạo ra các kiểu dáng linh hoạt hơn cho các trang web. Nó liên quan đến việc xử lý các quy tắc phụ thuộc vào điều kiện môi trường, như kích thước màn hình hoặc khả năng hỗ trợ tính năng.

### Cách sử dụng
Để sử dụng CSSConditionRule, bạn có thể truy cập nó thông qua thuộc tính `cssRules` của đối tượng `CSSStyleSheet`. Khi bạn đã xác định được quy tắc điều kiện, bạn có thể thao tác với nó bằng cách thêm, xóa hoặc sửa đổi các quy tắc con.

### Chi tiết
- **Thuộc tính**:
  - `conditionText`: Trả về chuỗi điều kiện (ví dụ: `max-width: 600px`).
  - `cssRules`: Trả về danh sách các quy tắc CSS bên trong điều kiện.
  
- **Phương thức**:
  - `insertRule()`: Thêm một quy tắc CSS mới vào trong điều kiện.
  - `deleteRule()`: Xóa một quy tắc CSS khỏi điều kiện.

## Ví dụ
```javascript
// Truy cập vào stylesheet đầu tiên
let sheet = document.styleSheets[0];

// Lặp qua các quy tắc trong stylesheet
for (let i = 0; i < sheet.cssRules.length; i++) {
    let rule = sheet.cssRules[i];

    // Kiểm tra xem quy tắc có phải là CSSConditionRule không
    if (rule instanceof CSSConditionRule) {
        console.log(rule.conditionText); // In ra điều kiện
        console.log(rule.cssRules.length); // In ra số quy tắc CSS bên trong
    }
}
```

## Giải thích
Khi làm việc với CSSConditionRule, có một số điều cần lưu ý:
- **Trình duyệt hỗ trợ**: Không phải tất cả các trình duyệt đều hỗ trợ đầy đủ các quy tắc điều kiện. Hãy kiểm tra tính tương thích trước khi triển khai.
- **Thao tác quy tắc**: Khi thêm hoặc xóa quy tắc, bạn cần đảm bảo rằng bạn không vi phạm cú pháp CSS, điều này có thể dẫn đến lỗi khi trình duyệt cố gắng áp dụng quy tắc.

## Tóm tắt một dòng
CSSConditionRule trong JavaScript cho phép bạn truy cập và quản lý các quy tắc CSS có điều kiện, góp phần tạo ra thiết kế linh hoạt cho trang web.