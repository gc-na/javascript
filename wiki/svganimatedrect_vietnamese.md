<!--
Meta Description: # SVGAnimatedRect trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ Cụ Thể ## Tóm tắt `SVGAnimatedRect` là một đối tượng trong SVG (Scalable Vector Graphi...
Meta Keywords: hình, nhật, chữ, svganimatedrect, một
-->

# SVGAnimatedRect trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ Cụ Thể

## Tóm tắt
`SVGAnimatedRect` là một đối tượng trong SVG (Scalable Vector Graphics) được sử dụng để biểu diễn các hình chữ nhật có thể thay đổi kích thước và vị trí theo thời gian. Trong JavaScript, đối tượng này cho phép lập trình viên điều khiển các thuộc tính hình chữ nhật một cách linh hoạt, hỗ trợ tạo ra các hiệu ứng động trong trang web.

## Tài liệu
### Mục đích
`SVGAnimatedRect` cung cấp một cách để làm việc với hình chữ nhật trong SVG, cho phép các thuộc tính như `x`, `y`, `width`, và `height` có thể được animate (hoạt hình) hoặc thay đổi theo thời gian.

### Cách sử dụng
`SVGAnimatedRect` có bốn thuộc tính chính:
- **baseVal**: Giá trị cơ bản của hình chữ nhật.
- **animVal**: Giá trị hiện tại của hình chữ nhật đang được animate.
- **x**: Vị trí x của hình chữ nhật.
- **y**: Vị trí y của hình chữ nhật.
- **width**: Chiều rộng của hình chữ nhật.
- **height**: Chiều cao của hình chữ nhật.

Để sử dụng `SVGAnimatedRect`, bạn cần phải tạo một phần tử SVG và sau đó truy cập nó qua DOM trong JavaScript.

### Ví dụ
Dưới đây là một ví dụ cơ bản về cách sử dụng `SVGAnimatedRect`:

```html
<svg width="200" height="200">
  <rect id="myRect" x="10" y="10" width="100" height="100" fill="blue" />
</svg>

<script>
  const rect = document.getElementById('myRect');
  
  // Truy cập các thuộc tính của SVGAnimatedRect
  console.log(rect.x.baseVal.value); // In ra giá trị x
  console.log(rect.width.baseVal.value); // In ra chiều rộng
  
  // Thay đổi thuộc tính
  rect.x.baseVal.value = 50; // Đặt vị trí x mới
  rect.width.baseVal.value = 150; // Đặt chiều rộng mới
</script>
```

### Giải thích
Khi làm việc với `SVGAnimatedRect`, có một số điểm cần lưu ý:
- **Thay đổi giá trị**: Khi bạn thay đổi một thuộc tính của `baseVal`, giá trị `animVal` sẽ không tự động cập nhật cho đến khi có một animation diễn ra.
- **Phân loại thuộc tính**: Hãy chắc chắn rằng bạn hiểu sự khác biệt giữa `baseVal` và `animVal`, vì chúng phục vụ các mục đích khác nhau trong quá trình hoạt hình.

### Tóm tắt một dòng
`SVGAnimatedRect` là đối tượng trong SVG cho phép điều khiển và animate các hình chữ nhật thông qua JavaScript, mang lại khả năng tương tác động cho đồ họa web.