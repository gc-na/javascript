<!--
Meta Description: # SVGAnimatedNumber trong JavaScript: Tìm Hiểu và Sử Dụng ## Tóm Tắt `SVGAnimatedNumber` là một interface trong SVG (Scalable Vector Graphics) cho phé...
Meta Keywords: circle, giá, trị, svg, trong
-->

# SVGAnimatedNumber trong JavaScript: Tìm Hiểu và Sử Dụng

## Tóm Tắt
`SVGAnimatedNumber` là một interface trong SVG (Scalable Vector Graphics) cho phép bạn làm việc với các giá trị số có thể hoạt động động, thường được sử dụng trong các thuộc tính SVG để tạo hiệu ứng hoạt hình.

## Tài Liệu
`SVGAnimatedNumber` được sử dụng để đại diện cho một giá trị số có thể thay đổi trong SVG. Nó chủ yếu được sử dụng cho các thuộc tính SVG mà có thể thay đổi theo thời gian, chẳng hạn như `cx`, `cy`, `r` trong các hình tròn hoặc `x1`, `y1`, `x2`, `y2` trong các đường thẳng.

### Cấu Trúc
`SVGAnimatedNumber` có hai thuộc tính quan trọng:
- `baseVal`: Giá trị gốc của thuộc tính, có thể được sử dụng để lấy hoặc thiết lập giá trị.
- `animVal`: Giá trị của thuộc tính hiện tại. Giá trị này có thể thay đổi khi có hoạt động động.

### Sử Dụng
Để sử dụng `SVGAnimatedNumber`, bạn cần truy cập các thuộc tính của một phần tử SVG. Ví dụ, khi bạn tạo một hình tròn bằng SVG, bạn có thể truy cập `cx` và `cy` như sau:

```javascript
let circle = document.createElementNS("http://www.w3.org/2000/svg", "circle");
circle.setAttribute("cx", "50");
circle.setAttribute("cy", "50");
circle.setAttribute("r", "40");
document.querySelector("svg").appendChild(circle);

// Truy cập SVGAnimatedNumber
let cx = circle.cx.animVal; // Giá trị hiện tại
let cy = circle.cy.baseVal;  // Giá trị gốc
```

## Ví Dụ
Dưới đây là một số ví dụ về cách sử dụng `SVGAnimatedNumber`:

### Ví dụ 1: Thay đổi giá trị động
```javascript
let circle = document.createElementNS("http://www.w3.org/2000/svg", "circle");
circle.setAttribute("cx", "50");
circle.setAttribute("cy", "50");
circle.setAttribute("r", "40");
document.querySelector("svg").appendChild(circle);

// Thay đổi giá trị cx
circle.cx.baseVal.value += 10; // Tăng giá trị cx lên 10
```

### Ví dụ 2: Hoạt hình với `requestAnimationFrame`
```javascript
let circle = document.createElementNS("http://www.w3.org/2000/svg", "circle");
circle.setAttribute("cx", "50");
circle.setAttribute("cy", "50");
circle.setAttribute("r", "40");
document.querySelector("svg").appendChild(circle);

let animation = () => {
    // Tăng giá trị cx theo thời gian
    circle.cx.baseVal.value += 1;
    if (circle.cx.baseVal.value < 100) {
        requestAnimationFrame(animation);
    }
};

requestAnimationFrame(animation);
```

## Giải Thích
Khi làm việc với `SVGAnimatedNumber`, bạn cần lưu ý rằng `baseVal` là giá trị bạn có thể thay đổi, trong khi `animVal` phản ánh giá trị hiện tại trong quá trình hoạt hình. Một số điểm cần lưu ý:
- `animVal` sẽ không thay đổi nếu không có hoạt hình thực sự diễn ra.
- Đảm bảo rằng bạn đang làm việc trong môi trường hỗ trợ SVG để tránh lỗi.

## Tóm Tắt Một Dòng
`SVGAnimatedNumber` cung cấp một cách linh hoạt để tương tác với các giá trị số động trong SVG, cho phép bạn tạo ra các hiệu ứng hoạt hình mượt mà.