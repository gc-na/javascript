<!--
Meta Description: # SVGLineElement trong JavaScript: Hướng Dẫn Chi Tiết ## Tóm tắt `SVGLineElement` là một đối tượng đại diện cho phần tử `<line>` trong SVG (Scalable V...
Meta Keywords: line, đường, thẳng, setattribute, svg
-->

# SVGLineElement trong JavaScript: Hướng Dẫn Chi Tiết

## Tóm tắt
`SVGLineElement` là một đối tượng đại diện cho phần tử `<line>` trong SVG (Scalable Vector Graphics), cho phép bạn vẽ các đường thẳng trên trang web bằng JavaScript.

## Tài liệu
### Mục đích
`SVGLineElement` được sử dụng để tạo và điều chỉnh đường thẳng trong SVG. Nó cho phép lập trình viên tùy chỉnh các thuộc tính như tọa độ bắt đầu và kết thúc của đường, màu sắc, độ dày, và nhiều thuộc tính khác.

### Cách sử dụng
Để sử dụng `SVGLineElement`, bạn cần tạo một phần tử SVG trong tài liệu HTML và sau đó sử dụng JavaScript để tạo một phần tử `line`. Dưới đây là cú pháp cơ bản:

```javascript
let svgNamespace = "http://www.w3.org/2000/svg";
let line = document.createElementNS(svgNamespace, "line");
line.setAttribute("x1", "10");
line.setAttribute("y1", "10");
line.setAttribute("x2", "100");
line.setAttribute("y2", "100");
line.setAttribute("stroke", "black");
line.setAttribute("stroke-width", "2");
```

### Chi tiết
- **Thuộc tính**:
  - `x1`, `y1`: Tọa độ điểm bắt đầu của đường thẳng.
  - `x2`, `y2`: Tọa độ điểm kết thúc của đường thẳng.
  - `stroke`: Màu sắc của đường thẳng.
  - `stroke-width`: Độ dày của đường thẳng.

- **Phương thức**:
  - `getTotalLength()`: Trả về độ dài tổng cộng của đường thẳng.
  - `getPointAtLength(length)`: Trả về điểm tại một vị trí nhất định dọc theo đường thẳng.

## Ví dụ
### Ví dụ 1: Tạo Đường Thẳng Cơ Bản
```html
<svg width="200" height="200">
    <line x1="10" y1="10" x2="190" y2="190" stroke="black" stroke-width="2" />
</svg>
```

### Ví dụ 2: Sử Dụng JavaScript Để Tạo Đường Thẳng
```html
<svg width="200" height="200" id="mySVG"></svg>
<script>
    let svgNamespace = "http://www.w3.org/2000/svg";
    let line = document.createElementNS(svgNamespace, "line");
    line.setAttribute("x1", "20");
    line.setAttribute("y1", "20");
    line.setAttribute("x2", "180");
    line.setAttribute("y2", "180");
    line.setAttribute("stroke", "red");
    line.setAttribute("stroke-width", "5");
    
    document.getElementById("mySVG").appendChild(line);
</script>
```

## Giải thích
Một số điểm cần lưu ý khi sử dụng `SVGLineElement`:
- Đảm bảo rằng bạn đang sử dụng không gian tên SVG khi tạo phần tử, nếu không JavaScript sẽ không nhận diện được phần tử này.
- Các tọa độ `x1`, `y1`, `x2`, `y2` cần phải là số và được chỉ định hợp lệ để tạo ra đường thẳng chính xác.
- Sử dụng các thuộc tính như `stroke` và `stroke-width` để tùy chỉnh hiển thị của đường thẳng.

## Tóm tắt một dòng
`SVGLineElement` là một phần tử trong SVG cho phép vẽ và điều chỉnh các đường thẳng trong JavaScript.