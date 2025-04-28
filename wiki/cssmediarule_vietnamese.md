<!--
Meta Description: # CSSMediaRule trong JavaScript: Hướng Dẫn Chi Tiết ## Tóm tắt CSSMediaRule là một đối tượng trong JavaScript cho phép lập trình viên tương tác với cá...
Meta Keywords: quy, tắc, các, media, rule
-->

# CSSMediaRule trong JavaScript: Hướng Dẫn Chi Tiết

## Tóm tắt
CSSMediaRule là một đối tượng trong JavaScript cho phép lập trình viên tương tác với các quy tắc CSS được áp dụng cho các điều kiện phương tiện khác nhau, chẳng hạn như kích thước màn hình hay loại thiết bị.

## Tài liệu
### Mục đích
CSSMediaRule cho phép bạn truy cập và chỉnh sửa các quy tắc CSS được định nghĩa trong một media query. Điều này rất hữu ích khi bạn cần thay đổi kiểu dáng của một trang web tùy thuộc vào điều kiện môi trường.

### Cách sử dụng
Để sử dụng CSSMediaRule, bạn cần truy cập nó thông qua đối tượng CSSStyleSheet. Bạn có thể tạo, sửa đổi hoặc xóa các quy tắc media trong stylesheet bằng cách sử dụng các phương thức như `insertRule` và `deleteRule`.

### Chi tiết
- **Thuộc tính**:
  - `media`: Trả về hoặc thiết lập điều kiện media của quy tắc này.
  - `cssRules`: Trả về danh sách các quy tắc CSS con thuộc về media rule hiện tại.
  
- **Phương thức**:
  - `insertRule(rule, index)`: Thêm một quy tắc CSS mới vào danh sách quy tắc.
  - `deleteRule(index)`: Xóa quy tắc CSS tại chỉ số đã chỉ định.

## Ví dụ
```javascript
// Lấy stylesheet đầu tiên
const stylesheet = document.styleSheets[0];

// Kiểm tra xem stylesheet có chứa media rules không
for (let i = 0; i < stylesheet.cssRules.length; i++) {
    const rule = stylesheet.cssRules[i];
    if (rule instanceof CSSMediaRule) {
        console.log(`Media Rule: ${rule.media.mediaText}`);
        
        // Thêm quy tắc mới vào media rule
        rule.insertRule('body { background-color: lightblue; }', rule.cssRules.length);
    }
}
```

## Giải thích
Khi làm việc với CSSMediaRule, có một số điểm cần lưu ý:
- **Trình duyệt không hỗ trợ**: Một số trình duyệt cũ có thể không hỗ trợ các phương thức hoặc thuộc tính này, vì vậy hãy kiểm tra tính tương thích trước khi sử dụng.
- **Thứ tự quy tắc**: Thứ tự của các quy tắc trong CSS có thể ảnh hưởng đến cách thức áp dụng chúng. Quy tắc được thêm sau sẽ ghi đè lên các quy tắc trước đó nếu chúng có cùng độ ưu tiên.
- **Lỗi khi xóa quy tắc**: Khi sử dụng `deleteRule`, hãy chắc chắn rằng bạn đang xóa đúng chỉ số, nếu không, sẽ xảy ra lỗi.

## Tóm tắt một dòng
CSSMediaRule trong JavaScript cho phép lập trình viên tương tác và quản lý các quy tắc CSS cho các điều kiện phương tiện khác nhau.