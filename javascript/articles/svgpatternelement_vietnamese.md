<!--
Meta Description: # SVGPatternElement trong JavaScript: Tạo Mẫu Họa Tiết Động ## Tóm tắt SVGPatternElement là một đối tượng trong SVG (Scalable Vector Graphics) cho phé...
Meta Keywords: pattern, setattribute, mẫu, svg, họa
-->

# SVGPatternElement trong JavaScript: Tạo Mẫu Họa Tiết Động

## Tóm tắt
SVGPatternElement là một đối tượng trong SVG (Scalable Vector Graphics) cho phép bạn tạo ra các mẫu họa tiết có thể được sử dụng để tô màu cho các hình dạng khác nhau trong tài liệu SVG, thông qua JavaScript.

## Tài liệu
SVGPatternElement là một phần mở rộng của SVG cho phép bạn định nghĩa các mẫu họa tiết mà có thể được lặp lại trên các hình dạng khác nhau. Đối tượng này được tạo ra bằng cách sử dụng thẻ `<pattern>` trong mã SVG. Mẫu họa tiết có thể bao gồm các hình dạng khác nhau như đường, hình tròn, hoặc hình chữ nhật, và có thể được điều chỉnh kích thước, vị trí và cách lặp lại.

### Cấu trúc
```html
<pattern id="myPattern" width="10" height="10" patternUnits="userSpaceOnUse">
  <circle cx="5" cy="5" r="5" fill="red" />
</pattern>
```

### Sử dụng
Để sử dụng SVGPatternElement trong JavaScript, bạn cần tạo và thêm nó vào tài liệu SVG của bạn. Dưới đây là các thuộc tính chính của SVGPatternElement:

- `id`: Định danh duy nhất cho mẫu họa tiết.
- `width` và `height`: Kích thước của mẫu họa tiết.
- `patternUnits`: Đơn vị đo lường cho mẫu (ví dụ: `userSpaceOnUse` hoặc `objectBoundingBox`).

### Cách tạo SVGPatternElement bằng JavaScript
```javascript
const svgNamespace = "http://www.w3.org/2000/svg";
const pattern = document.createElementNS(svgNamespace, "pattern");

pattern.setAttribute("id", "myPattern");
pattern.setAttribute("width", "10");
pattern.setAttribute("height", "10");
pattern.setAttribute("patternUnits", "userSpaceOnUse");

const circle = document.createElementNS(svgNamespace, "circle");
circle.setAttribute("cx", "5");
circle.setAttribute("cy", "5");
circle.setAttribute("r", "5");
circle.setAttribute("fill", "red");

pattern.appendChild(circle);
document.querySelector("defs").appendChild(pattern);
```

## Ví dụ
### Ví dụ 1: Sử dụng mẫu họa tiết để tô màu hình chữ nhật
```html
<svg width="200" height="200">
  <defs>
    <pattern id="myPattern" width="10" height="10" patternUnits="userSpaceOnUse">
      <circle cx="5" cy="5" r="5" fill="red" />
    </pattern>
  </defs>
  <rect width="200" height="200" fill="url(#myPattern)" />
</svg>
```

### Ví dụ 2: Tạo mẫu họa tiết với JavaScript
```javascript
const svg = document.querySelector("svg");
const defs = document.createElementNS(svgNamespace, "defs");

const pattern = document.createElementNS(svgNamespace, "pattern");
pattern.setAttribute("id", "myPattern");
pattern.setAttribute("width", "20");
pattern.setAttribute("height", "20");

const rect = document.createElementNS(svgNamespace, "rect");
rect.setAttribute("width", "20");
rect.setAttribute("height", "20");
rect.setAttribute("fill", "blue");

pattern.appendChild(rect);
defs.appendChild(pattern);
svg.appendChild(defs);

const rectFill = document.createElementNS(svgNamespace, "rect");
rectFill.setAttribute("width", "200");
rectFill.setAttribute("height", "200");
rectFill.setAttribute("fill", "url(#myPattern)");
svg.appendChild(rectFill);
```

## Giải thích
Khi sử dụng SVGPatternElement, có một số điều bạn cần lưu ý:

- **Kích thước mẫu**: Đảm bảo rằng kích thước mẫu được xác định chính xác để tránh tình trạng mẫu không lặp lại một cách hợp lý.
- **Biến đổi**: Nếu bạn áp dụng biến đổi trên hình dạng chứa mẫu họa tiết, nó có thể ảnh hưởng đến cách mà mẫu được hiển thị.
- **Thời gian tải**: Mẫu họa tiết có thể làm tăng thời gian tải nếu quá phức tạp hoặc có nhiều đối tượng con.

## Tóm tắt một dòng
SVGPatternElement trong JavaScript cho phép bạn tạo ra các mẫu họa tiết động để tô màu cho các hình dạng SVG.