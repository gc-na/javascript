<!--
Meta Description: # SVGPolylineElement trong JavaScript: Hướng dẫn chi tiết và ví dụ ## Tóm tắt `SVGPolylineElement` là một đối tượng trong JavaScript đại diện cho phần...
Meta Keywords: polyline, các, trong, một, svg
-->

# SVGPolylineElement trong JavaScript: Hướng dẫn chi tiết và ví dụ

## Tóm tắt
`SVGPolylineElement` là một đối tượng trong JavaScript đại diện cho phần tử `<polyline>` trong SVG (Scalable Vector Graphics), cho phép bạn vẽ các đoạn thẳng nối liền với nhau để tạo thành hình dạng phức tạp.

## Tài liệu
`SVGPolylineElement` kế thừa từ `SVGGeometryElement` và cung cấp các phương thức và thuộc tính để thao tác với phần tử `<polyline>`. Phần tử này được sử dụng để vẽ các đoạn thẳng nối với nhau, rất hữu ích trong việc tạo ra các hình vẽ vector.

### Mục đích
Mục đích chính của `SVGPolylineElement` là cung cấp một cách dễ dàng để vẽ các polyline trong SVG, cho phép lập trình viên tạo ra các biểu đồ, đồ thị, và hình dạng phức tạp với độ chính xác cao.

### Cách sử dụng
Bạn có thể tạo một đối tượng `SVGPolylineElement` bằng cách sử dụng phương thức `createElementNS` của đối tượng `SVGSVGElement`. Dưới đây là cú pháp cơ bản:

```javascript
const svgNamespace = "http://www.w3.org/2000/svg";
const polyline = document.createElementNS(svgNamespace, "polyline");
```

Sau khi tạo, bạn có thể thiết lập các thuộc tính như `points`, `stroke`, và `fill` để điều chỉnh cách hiển thị của polyline:

```javascript
polyline.setAttribute("points", "50,150 150,50 250,150");
polyline.setAttribute("stroke", "black");
polyline.setAttribute("fill", "none");
```

### Các thuộc tính chính
- **points**: Một chuỗi các giá trị tọa độ (x,y) phân tách bởi khoảng trắng hoặc dấu phẩy, xác định các điểm mà polyline sẽ đi qua.
- **stroke**: Màu sắc của đường viền polyline.
- **fill**: Màu sắc bên trong polyline (thường sẽ là "none" cho polyline).

## Ví dụ
Dưới đây là một ví dụ đơn giản về cách tạo và hiển thị một polyline trong HTML:

```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SVG Polyline Example</title>
</head>
<body>
    <svg width="300" height="200">
        <polyline points="50,150 150,50 250,150" stroke="black" fill="none" stroke-width="2"/>
    </svg>
</body>
</html>
```

## Giải thích
Khi làm việc với `SVGPolylineElement`, có một số điểm cần lưu ý:

- **Định dạng tọa độ**: Các tọa độ trong thuộc tính `points` cần phải được định dạng chính xác; nếu không, polyline có thể không hiển thị như mong muốn.
- **Chạy trên các trình duyệt**: Hãy kiểm tra tính tương thích giữa các trình duyệt, vì không phải tất cả các tính năng SVG đều được hỗ trợ đồng nhất.
- **Sự kết hợp với CSS**: Bạn có thể sử dụng CSS để điều chỉnh các thuộc tính như `stroke-width` và màu sắc, tuy nhiên, một số thuộc tính chỉ có thể được thiết lập trực tiếp thông qua JavaScript.

## Tóm tắt một dòng
`SVGPolylineElement` trong JavaScript cho phép bạn dễ dàng vẽ các đoạn thẳng nối với nhau trong SVG, tạo ra nhiều hình dạng phức tạp và biểu đồ trực quan.