<!--
Meta Description: # DOMRect trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ ## Tóm tắt DOMRect là một đối tượng trong JavaScript dùng để mô tả hình chữ nhật trong không g...
Meta Keywords: của, hình, chữ, nhật, domrect
-->

# DOMRect trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ

## Tóm tắt
DOMRect là một đối tượng trong JavaScript dùng để mô tả hình chữ nhật trong không gian hai chiều, thường được sử dụng để xác định vị trí và kích thước của các phần tử trên trang web.

## Tài liệu
### Mục đích
DOMRect cung cấp thông tin về hình dạng và vị trí của một phần tử DOM, bao gồm các thuộc tính như chiều rộng, chiều cao, và tọa độ của hình chữ nhật.

### Cách sử dụng
DOMRect thường được tạo ra từ phương thức `getBoundingClientRect()` của một phần tử DOM. Khi được gọi, phương thức này sẽ trả về một đối tượng DOMRect chứa thông tin về hình chữ nhật bao quanh phần tử.

### Các thuộc tính quan trọng
- **width**: Chiều rộng của hình chữ nhật.
- **height**: Chiều cao của hình chữ nhật.
- **top**: Tọa độ Y của cạnh trên cùng của hình chữ nhật.
- **right**: Tọa độ X của cạnh bên phải của hình chữ nhật.
- **bottom**: Tọa độ Y của cạnh dưới cùng của hình chữ nhật.
- **left**: Tọa độ X của cạnh bên trái của hình chữ nhật.

### Ví dụ
```javascript
// Lấy phần tử DOM
const element = document.getElementById('myElement');

// Lấy thông tin DOMRect
const rect = element.getBoundingClientRect();

// In ra thông tin
console.log('Chiều rộng:', rect.width);
console.log('Chiều cao:', rect.height);
console.log('Tọa độ trái:', rect.left);
console.log('Tọa độ trên:', rect.top);
```

## Giải thích
- **Những cạm bẫy và lưu ý**: 
  - DOMRect chỉ phản ánh kích thước và vị trí tại thời điểm phương thức `getBoundingClientRect()` được gọi. Nếu bạn thay đổi kích thước hoặc vị trí của phần tử sau khi gọi phương thức này mà không gọi lại, thông tin có thể không chính xác.
  - Tọa độ trả về là tương đối so với viewport, không phải so với tài liệu. Điều này có thể gây nhầm lẫn khi cần tính toán vị trí trong tài liệu tổng thể.

## Tóm tắt một dòng
DOMRect trong JavaScript là một đối tượng mô tả kích thước và vị trí của phần tử DOM, thường được lấy thông qua phương thức `getBoundingClientRect()`.