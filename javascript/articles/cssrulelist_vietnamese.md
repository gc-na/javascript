<!--
Meta Description: # Tìm Hiểu Về CSSRuleList Trong JavaScript: Cấu Trúc và Cách Sử Dụng ## Tóm tắt CSSRuleList là một đối tượng trong JavaScript dùng để đại diện cho dan...
Meta Keywords: quy, tắc, stylesheet, rules, css
-->

# Tìm Hiểu Về CSSRuleList Trong JavaScript: Cấu Trúc và Cách Sử Dụng

## Tóm tắt
CSSRuleList là một đối tượng trong JavaScript dùng để đại diện cho danh sách các quy tắc CSS trong một stylesheet. Nó cho phép lập trình viên truy cập và thao tác với các quy tắc CSS thông qua JavaScript.

## Tài liệu
### Mục đích
CSSRuleList được sử dụng để truy xuất và quản lý các quy tắc CSS trong các tài liệu HTML. Khi làm việc với CSS qua JavaScript, CSSRuleList giúp lập trình viên có thể điều chỉnh giao diện của trang web một cách linh hoạt và hiệu quả.

### Cách sử dụng
CSSRuleList không phải là một đối tượng có thể được tạo ra trực tiếp mà thay vào đó, nó được truy cập thông qua thuộc tính `cssRules` hoặc `rules` của đối tượng `CSSStyleSheet`. Dưới đây là cú pháp cơ bản để truy cập CSSRuleList:

```javascript
var stylesheet = document.styleSheets[0]; // Lấy stylesheet đầu tiên
var rules = stylesheet.cssRules || stylesheet.rules; // Lấy danh sách quy tắc CSS
```

### Chi tiết
- **cssRules**: Thuộc tính này trả về một CSSRuleList chứa tất cả các quy tắc CSS trong stylesheet.
- **rules**: Tương tự như cssRules, nhưng chủ yếu được sử dụng trong các trình duyệt cũ hơn.

Mỗi quy tắc trong CSSRuleList có thể được truy cập thông qua chỉ số, giống như một mảng. Bạn có thể duyệt qua các quy tắc bằng vòng lặp `for`.

## Ví dụ
### Ví dụ 1: Lấy và hiển thị các quy tắc CSS
```javascript
var stylesheet = document.styleSheets[0];
var rules = stylesheet.cssRules || stylesheet.rules;

for (var i = 0; i < rules.length; i++) {
    console.log(rules[i].cssText); // In ra quy tắc CSS
}
```

### Ví dụ 2: Thay đổi một quy tắc CSS
```javascript
var stylesheet = document.styleSheets[0];
var rules = stylesheet.cssRules || stylesheet.rules;

if (rules.length > 0) {
    rules[0].style.color = 'red'; // Đổi màu chữ của quy tắc đầu tiên thành đỏ
}
```

## Giải thích
- **Những cạm bẫy**: Một số trình duyệt có thể không hỗ trợ thuộc tính `cssRules` hoặc `rules`, vì vậy việc kiểm tra tính khả dụng là cần thiết.
- **Lưu ý**: Khi thay đổi các quy tắc CSS, cần cẩn thận để không làm ảnh hưởng đến giao diện tổng thể của trang. Một số quy tắc có thể bị ghi đè hoặc không áp dụng như mong đợi.

## Tóm tắt một câu
CSSRuleList là đối tượng trong JavaScript cho phép quản lý và thao tác với danh sách các quy tắc CSS trong stylesheet.