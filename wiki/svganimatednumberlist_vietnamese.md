<!--
Meta Description: # SVGAnimatedNumberList trong JavaScript: Hướng Dẫn Chi Tiết ## Tóm Tắt `SVGAnimatedNumberList` là một đối tượng trong JavaScript dùng để đại diện cho...
Meta Keywords: các, svg, svganimatednumberlist, giá, trị
-->

# SVGAnimatedNumberList trong JavaScript: Hướng Dẫn Chi Tiết

## Tóm Tắt
`SVGAnimatedNumberList` là một đối tượng trong JavaScript dùng để đại diện cho danh sách các số động trong SVG (Scalable Vector Graphics), cho phép bạn thao tác với các giá trị số này theo cách tương tác và động.

## Tài Liệu
### Mục Đích
`SVGAnimatedNumberList` được sử dụng để quản lý và cập nhật danh sách các giá trị số trong các thuộc tính SVG, giúp cải thiện khả năng lập trình động cho các đối tượng SVG trong trình duyệt.

### Cách Sử Dụng
`SVGAnimatedNumberList` thường được sử dụng trong các thuộc tính SVG như `stroke-dasharray` hoặc `patternUnits`. Đối tượng này có hai thuộc tính chính:

- `baseVal`: Trả về danh sách các số không thay đổi.
- `animVal`: Trả về danh sách các số đã được thay đổi bởi các hiệu ứng hoạt hình.

### Chi Tiết
Đối tượng `SVGAnimatedNumberList` không thể được tạo ra một cách trực tiếp. Nó thường được truy cập thông qua các thuộc tính của các phần tử SVG. Ví dụ, khi bạn làm việc với phần tử `SVGPathElement`, bạn có thể lấy `SVGAnimatedNumberList` từ thuộc tính `strokeDasharray`.

```javascript
const pathElement = document.getElementById('myPath');
const dashArray = pathElement.getTotalLength(); // Lấy chiều dài tổng thể của đường dẫn
```

## Ví Dụ
### Ví Dụ 1: Lấy giá trị từ `strokeDasharray`
```html
<svg width="200" height="200">
  <path id="myPath" d="M10 10 H 90 V 90 H 10 L 10 10" stroke="black" fill="transparent" stroke-dasharray="5,5"/>
</svg>

<script>
  const pathElement = document.getElementById('myPath');
  const strokeDashArray = pathElement.style.strokeDasharray; // Lấy giá trị strokeDasharray
  console.log(strokeDashArray); // Kết quả: "5,5"
</script>
```

### Ví Dụ 2: Cập nhật giá trị `strokeDasharray`
```html
<svg width="200" height="200">
  <path id="myPath" d="M10 10 H 90 V 90 H 10 L 10 10" stroke="black" fill="transparent" stroke-dasharray="5,5"/>
</svg>

<script>
  const pathElement = document.getElementById('myPath');
  pathElement.style.strokeDasharray = "10,5"; // Cập nhật giá trị strokeDasharray
</script>
```

## Giải Thích
Khi làm việc với `SVGAnimatedNumberList`, bạn cần lưu ý một số điểm sau:

- **Không thể khởi tạo trực tiếp**: Bạn không thể tạo một đối tượng `SVGAnimatedNumberList` mới; nó chỉ có thể được truy cập qua các phần tử SVG.
- **Tính tương thích trình duyệt**: Đảm bảo rằng trình duyệt bạn đang sử dụng hỗ trợ SVG và các thuộc tính liên quan đến nó.
- **Thay đổi giá trị**: Các thay đổi giá trị không tự động cập nhật đối tượng `animVal` cho đến khi có một hoạt ảnh được kích hoạt.

## Tóm Tắt Một Dòng
`SVGAnimatedNumberList` là một đối tượng trong JavaScript cho phép quản lý danh sách số trong các thuộc tính SVG, cung cấp khả năng tương tác động cho các giá trị này.