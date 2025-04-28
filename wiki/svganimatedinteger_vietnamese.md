<!--
Meta Description: # SVGAnimatedInteger trong JavaScript: Hướng dẫn chi tiết và ví dụ ## Tóm tắt `SVGAnimatedInteger` là một đối tượng trong JavaScript, thuộc về API SVG...
Meta Keywords: các, giá, trị, thuộc, svg
-->

# SVGAnimatedInteger trong JavaScript: Hướng dẫn chi tiết và ví dụ

## Tóm tắt
`SVGAnimatedInteger` là một đối tượng trong JavaScript, thuộc về API SVG, cho phép quản lý các giá trị số có thể thay đổi trong các thuộc tính SVG. Đối tượng này hữu ích khi làm việc với các thuộc tính động trong đồ họa SVG.

## Tài liệu
### Mục đích
`SVGAnimatedInteger` được sử dụng để định nghĩa một giá trị số mà có thể thay đổi theo thời gian hoặc thông qua các tương tác của người dùng. Nó thường xuất hiện trong các thuộc tính của các phần tử SVG, chẳng hạn như chiều rộng, chiều cao hoặc các tọa độ.

### Cách sử dụng
Đối tượng `SVGAnimatedInteger` chứa hai thuộc tính quan trọng:
- `baseVal`: Giá trị cơ bản của thuộc tính, được lưu trữ dưới dạng một số nguyên.
- `animVal`: Giá trị hiện tại của thuộc tính, có thể khác với `baseVal` nếu có hoạt ảnh đang diễn ra.

### Chi tiết
Khi làm việc với `SVGAnimatedInteger`, bạn có thể nhận giá trị của `baseVal` và `animVal` để xác định giá trị hiện tại của thuộc tính. Điều này rất hữu ích trong các ứng dụng SVG động, nơi mà các thuộc tính có thể thay đổi liên tục.

## Ví dụ
```javascript
// Tạo một phần tử SVG
let svgNS = "http://www.w3.org/2000/svg"; 
let circle = document.createElementNS(svgNS, "circle");
circle.setAttribute("cx", 50);
circle.setAttribute("cy", 50);
circle.setAttribute("r", 40);
circle.setAttribute("fill", "red");

// Thêm vào tài liệu
document.getElementById("svgContainer").appendChild(circle);

// Truy cập vào thuộc tính SVGAnimatedInteger
let radius = circle.r.baseVal; // Giá trị cơ bản
console.log(radius.value); // In ra giá trị bán kính

// Cập nhật giá trị bán kính
radius.value = 60; 
console.log(circle.r.animVal.value); // In ra giá trị hiện tại
```

## Giải thích
Khi làm việc với `SVGAnimatedInteger`, có một số điểm cần lưu ý:
- Giá trị `animVal` chỉ thay đổi khi có hoạt ảnh diễn ra; nếu không có hoạt ảnh, `baseVal` và `animVal` sẽ bằng nhau.
- Một số trình duyệt có thể xử lý các hoạt ảnh SVG khác nhau, vì vậy hãy kiểm tra khả năng tương thích khi sử dụng `SVGAnimatedInteger`.

## Tóm tắt một dòng
`SVGAnimatedInteger` cho phép quản lý các giá trị số động trong thuộc tính SVG, hỗ trợ việc tạo ra các đồ họa SVG tương tác và hấp dẫn.