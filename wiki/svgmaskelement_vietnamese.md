<!--
Meta Description: # SVGMaskElement trong JavaScript: Hướng dẫn chi tiết và ứng dụng ## Tóm tắt `SVGMaskElement` là một phần của API SVG trong JavaScript, cho phép định ...
Meta Keywords: setattribute, svg, mặt, mask, rect
-->

# SVGMaskElement trong JavaScript: Hướng dẫn chi tiết và ứng dụng

## Tóm tắt
`SVGMaskElement` là một phần của API SVG trong JavaScript, cho phép định nghĩa và sử dụng mặt nạ cho các đối tượng SVG, giúp tạo ra các hiệu ứng hình ảnh phong phú và phức tạp.

## Tài liệu
### Mục đích
`SVGMaskElement` được sử dụng để tạo mặt nạ cho các đối tượng SVG. Mặt nạ cho phép bạn hiển thị một phần của hình ảnh hoặc đối tượng trong khi ẩn các phần khác. Điều này rất hữu ích trong việc tạo ra các hiệu ứng hình ảnh độc đáo và đẹp mắt.

### Cách sử dụng
`SVGMaskElement` có thể được khai báo trong tài liệu SVG bằng cách sử dụng thẻ `<mask>`. Để sử dụng mặt nạ này trong JavaScript, bạn có thể truy cập và thao tác với các thuộc tính của nó thông qua DOM. 

Dưới đây là một số thuộc tính quan trọng của `SVGMaskElement`:
- `maskUnits`: Xác định đơn vị cho mặt nạ (ví dụ: `userSpaceOnUse` hoặc `objectBoundingBox`).
- `x`, `y`, `width`, `height`: Xác định hình dạng và kích thước của mặt nạ.

### Cú pháp
```javascript
const maskElement = document.createElementNS("http://www.w3.org/2000/svg", "mask");
maskElement.setAttribute("id", "myMask");
maskElement.setAttribute("maskUnits", "userSpaceOnUse");
maskElement.setAttribute("x", "0");
maskElement.setAttribute("y", "0");
maskElement.setAttribute("width", "100");
maskElement.setAttribute("height", "100");
```

## Ví dụ
### Ví dụ 1: Tạo mặt nạ đơn giản
```html
<svg width="200" height="200">
  <defs>
    <mask id="myMask">
      <rect x="0" y="0" width="100" height="100" fill="white" />
      <circle cx="50" cy="50" r="50" fill="black" />
    </mask>
  </defs>
  <rect x="0" y="0" width="200" height="200" fill="blue" mask="url(#myMask)" />
</svg>
```

### Ví dụ 2: Sử dụng mặt nạ trong JavaScript
```javascript
const svgNS = "http://www.w3.org/2000/svg";
const mask = document.createElementNS(svgNS, "mask");
mask.setAttribute("id", "mask1");

const rect = document.createElementNS(svgNS, "rect");
rect.setAttribute("x", "0");
rect.setAttribute("y", "0");
rect.setAttribute("width", "100");
rect.setAttribute("height", "100");
rect.setAttribute("fill", "white");

const circle = document.createElementNS(svgNS, "circle");
circle.setAttribute("cx", "50");
circle.setAttribute("cy", "50");
circle.setAttribute("r", "50");
circle.setAttribute("fill", "black");

mask.appendChild(rect);
mask.appendChild(circle);
document.querySelector("svg defs").appendChild(mask);

const blueRect = document.createElementNS(svgNS, "rect");
blueRect.setAttribute("x", "0");
blueRect.setAttribute("y", "0");
blueRect.setAttribute("width", "200");
blueRect.setAttribute("height", "200");
blueRect.setAttribute("fill", "blue");
blueRect.setAttribute("mask", "url(#mask1)");

document.querySelector("svg").appendChild(blueRect);
```

## Giải thích
Khi làm việc với `SVGMaskElement`, có một số điều cần lưu ý:
- Đảm bảo rằng các thuộc tính của mặt nạ được thiết lập chính xác trước khi áp dụng cho các đối tượng SVG.
- Mặt nạ phải được định nghĩa trong phần `<defs>` của tài liệu SVG.
- Sử dụng các đơn vị đúng (như `userSpaceOnUse` hoặc `objectBoundingBox`) để đảm bảo mặt nạ hoạt động như mong muốn.

## Tóm tắt một dòng
`SVGMaskElement` trong JavaScript cho phép tạo và sử dụng mặt nạ cho các đối tượng SVG, mang đến những hiệu ứng hình ảnh độc đáo và sáng tạo.