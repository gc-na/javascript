<!--
Meta Description: # SVGLinearGradientElement: Sử Dụng Trong JavaScript Để Tạo Gradient Đường Thẳng ## Tóm tắt `SVGLinearGradientElement` là một phần của API SVG trong J...
Meta Keywords: stop, svg, gradient, các, màu
-->

# SVGLinearGradientElement: Sử Dụng Trong JavaScript Để Tạo Gradient Đường Thẳng

## Tóm tắt
`SVGLinearGradientElement` là một phần của API SVG trong JavaScript, cho phép lập trình viên tạo ra các gradient đường thẳng tùy chỉnh cho các hình dạng SVG. Gradient này có thể được sử dụng để tạo ra các hiệu ứng màu sắc phong phú và thu hút hơn cho đồ họa web.

## Tài Liệu
`SVGLinearGradientElement` là một đối tượng SVG đại diện cho một gradient đường thẳng. Nó cho phép bạn định nghĩa màu sắc và vị trí của các màu trong gradient, từ đó tạo ra các hiệu ứng chuyển màu mềm mại cho các đối tượng SVG như hình chữ nhật, hình tròn, hoặc bất kỳ hình dạng nào khác.

### Mục Đích
- Tạo gradient đường thẳng cho các hình dạng SVG.
- Cung cấp khả năng tùy chỉnh màu sắc và vị trí của từng màu trong gradient.

### Cách Sử Dụng
Để sử dụng `SVGLinearGradientElement`, bạn cần tạo một phần tử `<linearGradient>` trong tài liệu SVG của bạn. Bạn có thể thêm các phần tử `<stop>` bên trong để định nghĩa màu sắc và vị trí của chúng.

#### Cú Pháp
```html
<svg width="200" height="200">
  <defs>
    <linearGradient id="grad1" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:rgb(255,255,0);stop-opacity:1" />
      <stop offset="100%" style="stop-color:rgb(255,0,0);stop-opacity:1" />
    </linearGradient>
  </defs>
  <rect width="200" height="200" fill="url(#grad1)" />
</svg>
```

## Ví dụ
### Ví dụ Cơ Bản
```html
<svg width="300" height="300">
  <defs>
    <linearGradient id="gradient1" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:blue;stop-opacity:1" />
      <stop offset="100%" style="stop-color:red;stop-opacity:1" />
    </linearGradient>
  </defs>
  <circle cx="150" cy="150" r="100" fill="url(#gradient1)" />
</svg>
```
### Ví dụ Nâng Cao
```html
<svg width="500" height="500">
  <defs>
    <linearGradient id="gradient2" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:orange;stop-opacity:1" />
      <stop offset="50%" style="stop-color:yellow;stop-opacity:1" />
      <stop offset="100%" style="stop-color:green;stop-opacity:1" />
    </linearGradient>
  </defs>
  <rect width="500" height="500" fill="url(#gradient2)" />
</svg>
```

## Giải Thích
- **Thứ Tự Các Màu**: Các màu trong gradient được xác định theo thứ tự từ trên xuống dưới hoặc từ trái sang phải dựa trên các thuộc tính `x1`, `y1`, `x2`, `y2`.
- **Phần Tử `<stop>`**: Mỗi phần tử `<stop>` xác định một màu tại một vị trí cụ thể trong gradient bằng thuộc tính `offset`.
- **Lỗi Thường Gặp**: Một số lập trình viên có thể quên định nghĩa phần tử `<defs>` trước khi sử dụng gradient, dẫn đến việc gradient không hiển thị. Đảm bảo rằng phần tử `<linearGradient>` được định nghĩa trong `<defs>`.

## Tóm Tắt Một Dòng
`SVGLinearGradientElement` cho phép tạo ra gradient đường thẳng trong SVG, mang lại hiệu ứng màu sắc phong phú cho đồ họa web.