<!--
Meta Description: # SVGFEDistantLightElement trong JavaScript: Tạo Ánh Sáng Đặc Biệt cho Hình Ảnh SVG ## Tóm tắt SVGFEDistantLightElement là một phần của API SVG trong ...
Meta Keywords: svg, sáng, ánh, filter, trong
-->

# SVGFEDistantLightElement trong JavaScript: Tạo Ánh Sáng Đặc Biệt cho Hình Ảnh SVG

## Tóm tắt
SVGFEDistantLightElement là một phần của API SVG trong JavaScript, cho phép bạn xác định nguồn sáng theo kiểu ánh sáng xa cho các hiệu ứng hình ảnh trong SVG.

## Tài liệu
SVGFEDistantLightElement là một phần tử SVG được sử dụng trong các bộ lọc SVG để tạo ra hiệu ứng ánh sáng. Nó đặc biệt hữu ích trong việc tạo ra các hiệu ứng đổ bóng và làm nổi bật các hình ảnh SVG bằng cách mô phỏng ánh sáng từ một vị trí xa. 

### Mục đích
- Cung cấp một nguồn ánh sáng xa cho các bộ lọc SVG.
- Tạo ra các hiệu ứng hình ảnh sống động và chân thực hơn.

### Cách sử dụng
Để sử dụng SVGFEDistantLightElement, bạn cần tạo một phần tử trong tài liệu SVG của mình. Phần tử này thường được sử dụng bên trong phần tử `<filter>`.

```html
<svg width="200" height="200">
  <filter id="f1" x="0" y="0">
    <feDiffuseLighting in="SourceGraphic" lighting-color="white">
      <feDistantLight azimuth="45" elevation="55"/>
    </feDiffuseLighting>
  </filter>
  <rect width="200" height="200" fill="blue" filter="url(#f1)"/>
</svg>
```

### Tham số
- **azimuth**: Góc ánh sáng theo chiều ngang.
- **elevation**: Góc ánh sáng theo chiều dọc.

## Ví dụ
### Ví dụ 1: Tạo ánh sáng từ góc 45 độ
```html
<svg width="200" height="200">
  <filter id="f1">
    <feDiffuseLighting in="SourceGraphic" lighting-color="yellow">
      <feDistantLight azimuth="45" elevation="30"/>
    </feDiffuseLighting>
  </filter>
  <circle cx="100" cy="100" r="80" fill="orange" filter="url(#f1)"/>
</svg>
```

### Ví dụ 2: Ánh sáng từ góc 135 độ
```html
<svg width="200" height="200">
  <filter id="f2">
    <feDiffuseLighting in="SourceGraphic" lighting-color="red">
      <feDistantLight azimuth="135" elevation="45"/>
    </feDiffuseLighting>
  </filter>
  <rect x="20" y="20" width="160" height="160" fill="green" filter="url(#f2)"/>
</svg>
```

## Giải thích
Khi làm việc với SVGFEDistantLightElement, hãy chú ý đến các giá trị của azimuth và elevation. Nếu không thiết lập đúng, hiệu ứng ánh sáng có thể không hiển thị như mong đợi. Ngoài ra, không nên lạm dụng việc sử dụng quá nhiều ánh sáng trong một trang SVG vì điều này có thể làm giảm hiệu suất render của trình duyệt.

## Tóm tắt một dòng
SVGFEDistantLightElement trong JavaScript giúp tạo hiệu ứng ánh sáng xa cho hình ảnh SVG, mang lại sự sống động và chân thực cho các thiết kế đồ họa.