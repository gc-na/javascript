<!--
Meta Description: # SVGAnimatedPreserveAspectRatio trong JavaScript: Hướng dẫn chi tiết ## Tóm tắt `SVGAnimatedPreserveAspectRatio` là một giao diện trong SVG (Scalable...
Meta Keywords: hình, svg, ảnh, preserveaspectratio, của
-->

# SVGAnimatedPreserveAspectRatio trong JavaScript: Hướng dẫn chi tiết

## Tóm tắt
`SVGAnimatedPreserveAspectRatio` là một giao diện trong SVG (Scalable Vector Graphics) cho phép điều chỉnh cách thức mà hình ảnh SVG được phóng to hoặc thu nhỏ, đảm bảo rằng tỷ lệ khung hình của hình ảnh được bảo tồn.

## Tài liệu
### Mục đích
`SVGAnimatedPreserveAspectRatio` được sử dụng để quản lý và điều chỉnh tỷ lệ khung hình của một hình ảnh SVG khi nó được hiển thị. Nó cho phép các nhà phát triển kiểm soát cách thức hình ảnh được cân chỉnh và cắt xén trong không gian hiển thị.

### Cách sử dụng
Giao diện `SVGAnimatedPreserveAspectRatio` không được khởi tạo trực tiếp mà thường được truy cập thông qua các thuộc tính của đối tượng SVG, chẳng hạn như `preserveAspectRatio` trong các hình ảnh SVG.

### Thông tin chi tiết
- **Thuộc tính**: `baseVal` và `animVal`.
  - `baseVal`: Giá trị cơ sở của thuộc tính `preserveAspectRatio`.
  - `animVal`: Giá trị động, có thể thay đổi trong quá trình hoạt ảnh.

- **Giá trị**: Các giá trị của `preserveAspectRatio` bao gồm:
  - `none`: Không duy trì tỷ lệ khung hình.
  - `xMinYMin`, `xMidYMid`, `xMaxYMax`: Duy trì tỷ lệ khung hình và căn chỉnh hình ảnh theo các góc khác nhau.

## Ví dụ
### Ví dụ 1: Thiết lập `preserveAspectRatio` cho hình ảnh SVG
```html
<svg width="300" height="200">
    <image href="image.svg" width="100%" height="100%" preserveAspectRatio="xMinYMin meet" />
</svg>
```

### Ví dụ 2: Lấy giá trị của `preserveAspectRatio` bằng JavaScript
```javascript
const svgImage = document.querySelector('image');
const preserveAspectRatio = svgImage.preserveAspectRatio.baseVal;
console.log(preserveAspectRatio);
```

## Giải thích
Mặc dù `SVGAnimatedPreserveAspectRatio` có tính năng hữu ích, nhưng có một số điều cần lưu ý:
- Các giá trị `preserveAspectRatio` có thể không hoạt động như mong đợi nếu không đặt kích thước chính xác cho phần tử SVG.
- Nếu không có `preserveAspectRatio`, hình ảnh có thể bị biến dạng nếu không gian hiển thị không tương thích với tỷ lệ khung hình ban đầu của hình ảnh.
- Cần chú ý đến việc sử dụng các giá trị khớp với thiết kế tổng thể của SVG để tránh việc hình ảnh bị cắt xén không mong muốn.

## Tóm tắt một dòng
`SVGAnimatedPreserveAspectRatio` là một giao diện trong SVG giúp quản lý tỷ lệ khung hình của hình ảnh SVG khi được hiển thị trong JavaScript.