<!--
Meta Description: # CSSGroupingRule trong JavaScript: Hiểu Biết Cơ Bản và Cách Sử Dụng ## Tóm Tắt CSSGroupingRule là một đối tượng trong JavaScript đại diện cho các quy...
Meta Keywords: quy, tắc, các, trong, một
-->

# CSSGroupingRule trong JavaScript: Hiểu Biết Cơ Bản và Cách Sử Dụng

## Tóm Tắt
CSSGroupingRule là một đối tượng trong JavaScript đại diện cho các quy tắc nhóm trong CSS, bao gồm các quy tắc như @media và @supports. Đối tượng này cho phép lập trình viên truy cập và thao tác các quy tắc nhóm một cách dễ dàng trong tài liệu DOM.

## Tài Liệu
### Mục Đích
CSSGroupingRule cung cấp một cách để làm việc với các quy tắc nhóm trong CSS, cho phép lập trình viên tương tác với chúng thông qua JavaScript. Điều này rất hữu ích khi bạn cần thay đổi hoặc kiểm tra các quy tắc CSS dựa trên các điều kiện hoặc sự kiện cụ thể.

### Cách Sử Dụng
CSSGroupingRule thường được sử dụng trong các tình huống mà bạn cần truy cập hoặc thay đổi các quy tắc nhóm như @media hoặc @supports. Để làm việc với CSSGroupingRule, bạn thường sẽ truy cập qua đối tượng CSSStyleSheet.

### Chi Tiết
- **Thuộc Tính**:
  - `cssRules`: Trả về danh sách các quy tắc CSS trong nhóm.
  - `length`: Trả về số lượng quy tắc trong nhóm.

- **Phương Thức**:
  - `insertRule(rule, index)`: Thêm một quy tắc CSS mới vào vị trí chỉ định.
  - `deleteRule(index)`: Xóa quy tắc CSS tại vị trí chỉ định.

## Ví Dụ
### Ví Dụ Cơ Bản
```javascript
// Truy cập vào stylesheet đầu tiên
const stylesheet = document.styleSheets[0];

// Truy cập vào các quy tắc CSS
const cssRules = stylesheet.cssRules;

// Kiểm tra loại quy tắc
for (let i = 0; i < cssRules.length; i++) {
    if (cssRules[i] instanceof CSSGroupingRule) {
        console.log('Đây là một quy tắc nhóm:', cssRules[i].cssText);
    }
}

// Thêm một quy tắc mới vào nhóm @media
const mediaRule = cssRules[0]; // Giả sử đây là một quy tắc @media
mediaRule.insertRule('body { background-color: blue; }', mediaRule.cssRules.length);
```

## Giải Thích
Khi làm việc với CSSGroupingRule, có một số điều cần lưu ý:
- **Truy cập Quy Tắc**: Khi bạn sử dụng `cssRules`, hãy chắc chắn rằng bạn kiểm tra loại quy tắc trước khi thao tác, vì không phải tất cả các quy tắc đều là CSSGroupingRule.
- **Thay Đổi Quy Tắc**: Sử dụng `insertRule` và `deleteRule` cẩn thận, vì việc thay đổi quy tắc có thể ảnh hưởng đến cách mà CSS được áp dụng trên trang.

## Tóm Tắt Một Câu
CSSGroupingRule trong JavaScript cho phép lập trình viên quản lý và thao tác các quy tắc nhóm trong CSS, như @media và @supports, một cách hiệu quả.