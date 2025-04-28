<!--
Meta Description: # DOMRectReadOnly trong JavaScript: Đặc tả và Cách Sử Dụng ## Tóm tắt `DOMRectReadOnly` là một đối tượng trong JavaScript được sử dụng để đại diện cho...
Meta Keywords: của, trí, rect, domrectreadonly, thay
-->

# DOMRectReadOnly trong JavaScript: Đặc tả và Cách Sử Dụng

## Tóm tắt
`DOMRectReadOnly` là một đối tượng trong JavaScript được sử dụng để đại diện cho hình chữ nhật (rectangle) không thay đổi, thường được sử dụng để lấy thông tin về kích thước và vị trí của các phần tử trong tài liệu HTML.

## Tài liệu
### Mục đích
`DOMRectReadOnly` cung cấp một cách để truy cập thông tin về hình chữ nhật mà không cho phép thay đổi thuộc tính của nó. Đối tượng này thường được quay ngược từ các phương thức như `getBoundingClientRect()`.

### Cách sử dụng
Để tạo một đối tượng `DOMRectReadOnly`, bạn thường không tạo nó trực tiếp. Thay vào đó, bạn có thể lấy nó thông qua các phương thức của DOM. Ví dụ:

```javascript
const element = document.getElementById('myElement');
const rect = element.getBoundingClientRect();
```

### Chi tiết
`DOMRectReadOnly` có các thuộc tính sau:
- `x`: Vị trí x của góc trên bên trái.
- `y`: Vị trí y của góc trên bên trái.
- `width`: Chiều rộng của hình chữ nhật.
- `height`: Chiều cao của hình chữ nhật.
- `top`: Vị trí y của cạnh trên.
- `right`: Vị trí x của cạnh bên phải.
- `bottom`: Vị trí y của cạnh dưới.
- `left`: Vị trí x của cạnh trái.

Các thuộc tính này đều là các thuộc tính số và không thể thay đổi.

## Ví dụ
### Ví dụ 1: Lấy kích thước và vị trí của một phần tử
```javascript
const element = document.getElementById('myElement');
const rect = element.getBoundingClientRect();

console.log(`Width: ${rect.width}, Height: ${rect.height}`);
console.log(`Top: ${rect.top}, Left: ${rect.left}`);
```

### Ví dụ 2: Sử dụng với nhiều phần tử
```javascript
const elements = document.querySelectorAll('.myClass');
elements.forEach(element => {
    const rect = element.getBoundingClientRect();
    console.log(`Element: ${element.tagName}, Width: ${rect.width}, Height: ${rect.height}`);
});
```

## Giải thích
- **Những cạm bẫy phổ biến**: Một số lập trình viên có thể nhầm lẫn rằng `DOMRectReadOnly` có thể thay đổi. Tuy nhiên, đối tượng này chỉ hỗ trợ đọc, không hỗ trợ ghi.
- **Chú ý về kích thước**: Kích thước của hình chữ nhật có thể thay đổi khi trang được cuộn hoặc thay đổi kích thước. Do đó, bạn nên gọi `getBoundingClientRect()` mỗi khi bạn cần thông tin mới nhất về kích thước và vị trí.
- **Tương thích**: `DOMRectReadOnly` được hỗ trợ trên hầu hết các trình duyệt hiện đại, nhưng bạn nên kiểm tra tính tương thích nếu ứng dụng của bạn cần hỗ trợ các trình duyệt cũ.

## Tóm tắt một dòng
`DOMRectReadOnly` là một đối tượng trong JavaScript giúp truy cập thông tin về kích thước và vị trí của phần tử mà không cho phép thay đổi thuộc tính của nó.