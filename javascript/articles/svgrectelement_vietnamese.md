<!--
Meta Description: # SVGRectElement trong JavaScript: Tạo và Điều Khiển Hình Chữ Nhật ## Tóm tắt `SVGRectElement` là một đối tượng trong JavaScript dùng để tạo và quản l...
Meta Keywords: hình, chữ, nhật, rect, svg
-->

# SVGRectElement trong JavaScript: Tạo và Điều Khiển Hình Chữ Nhật

## Tóm tắt
`SVGRectElement` là một đối tượng trong JavaScript dùng để tạo và quản lý hình chữ nhật trong tài liệu SVG (Scalable Vector Graphics). Nó cung cấp các thuộc tính và phương thức cho phép lập trình viên thao tác với hình chữ nhật một cách dễ dàng.

## Tài liệu
`SVGRectElement` là một phần của DOM (Document Object Model) trong SVG. Đối tượng này đại diện cho một hình chữ nhật trong không gian SVG và cung cấp nhiều thuộc tính cho phép bạn tùy chỉnh kích thước, vị trí và các thuộc tính khác của hình chữ nhật.

### Mục đích
Mục đích chính của `SVGRectElement` là tạo ra các hình chữ nhật trong SVG và cho phép lập trình viên điều chỉnh các thuộc tính như vị trí, chiều rộng, chiều cao, và các thuộc tính kiểu dáng như màu sắc, viền, và độ mờ.

### Cách sử dụng
Để sử dụng `SVGRectElement`, bạn có thể tạo một đối tượng hình chữ nhật mới bằng cách sử dụng phương thức `createElementNS` của đối tượng `document`. Dưới đây là cú pháp cơ bản:

```javascript
const svgNamespace = "http://www.w3.org/2000/svg";
const rect = document.createElementNS(svgNamespace, "rect");
rect.setAttribute("x", "10");
rect.setAttribute("y", "10");
rect.setAttribute("width", "100");
rect.setAttribute("height", "50");
rect.setAttribute("fill", "blue");
```

Sau khi tạo ra đối tượng `SVGRectElement`, bạn có thể thêm nó vào một phần tử SVG trong tài liệu HTML để hiển thị hình chữ nhật.

### Các thuộc tính quan trọng
- `x`: Vị trí phía trên bên trái của hình chữ nhật.
- `y`: Vị trí phía trên bên trái của hình chữ nhật.
- `width`: Chiều rộng của hình chữ nhật.
- `height`: Chiều cao của hình chữ nhật.
- `fill`: Màu sắc của hình chữ nhật.

## Ví dụ
### Ví dụ cơ bản
Dưới đây là một ví dụ đơn giản về cách tạo hình chữ nhật trong SVG:

```html
<svg width="200" height="200">
    <rect x="10" y="10" width="100" height="50" fill="green" />
</svg>
```

### Ví dụ nâng cao
Bạn có thể thay đổi màu sắc và kích thước của hình chữ nhật bằng JavaScript:

```html
<svg id="mySvg" width="200" height="200">
</svg>

<script>
    const svgNamespace = "http://www.w3.org/2000/svg";
    const rect = document.createElementNS(svgNamespace, "rect");
    rect.setAttribute("x", "10");
    rect.setAttribute("y", "10");
    rect.setAttribute("width", "100");
    rect.setAttribute("height", "50");
    rect.setAttribute("fill", "red");
    
    document.getElementById("mySvg").appendChild(rect);
    
    // Thay đổi thuộc tính sau 2 giây
    setTimeout(() => {
        rect.setAttribute("fill", "blue");
        rect.setAttribute("width", "150");
    }, 2000);
</script>
```

## Giải thích
Khi sử dụng `SVGRectElement`, có một số điều cần lưu ý:
- Nếu bạn không chỉ định thuộc tính `x` và `y`, hình chữ nhật sẽ mặc định nằm ở vị trí (0,0).
- Các thuộc tính `width` và `height` phải là số dương, nếu không, hình chữ nhật sẽ không hiển thị.
- Đảm bảo rằng bạn sử dụng đúng không gian tên SVG khi tạo đối tượng bằng phương thức `createElementNS`.

## Tóm tắt một dòng
`SVGRectElement` là một đối tượng JavaScript cho phép tạo và điều chỉnh hình chữ nhật trong SVG với nhiều thuộc tính tùy chỉnh.