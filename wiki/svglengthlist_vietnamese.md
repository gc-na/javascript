<!--
Meta Description: # SVGLengthList: Danh sách chiều dài SVG trong JavaScript ## Tóm tắt SVGLengthList là một đối tượng trong JavaScript cho phép quản lý danh sách các ch...
Meta Keywords: các, một, chiều, dài, đối
-->

# SVGLengthList: Danh sách chiều dài SVG trong JavaScript

## Tóm tắt
SVGLengthList là một đối tượng trong JavaScript cho phép quản lý danh sách các chiều dài (length) của các thuộc tính SVG. Đối tượng này hỗ trợ các thao tác như thêm, xóa và truy xuất các giá trị chiều dài, rất hữu ích trong việc làm việc với các hình ảnh vector trong các ứng dụng web.

## Tài liệu
SVGLengthList được sử dụng để tạo và quản lý danh sách các đối tượng SVGLength. Mỗi đối tượng SVGLength đại diện cho một chiều dài có thể được sử dụng để định nghĩa kích thước của các hình dạng SVG như đường thẳng, hình chữ nhật, và các hình dạng khác.

### Mục đích
- Cung cấp một cách để làm việc với nhiều chiều dài trong SVG.
- Hỗ trợ các thao tác như thêm, xóa và truy xuất chiều dài.

### Cách sử dụng
Để sử dụng SVGLengthList, bạn cần truy cập vào thuộc tính `svgLengthList` của một đối tượng SVG cụ thể. Ví dụ, thuộc tính này có thể được tìm thấy trong các thuộc tính như `stroke-dasharray`, `width`, hoặc `height`.

### Chi tiết
- **Thuộc tính**: 
  - `numberOfItems`: trả về số lượng phần tử trong danh sách.
  - `appendItem(newItem)`: thêm một đối tượng SVGLength mới vào cuối danh sách.
  - `clear()`: xóa tất cả các phần tử trong danh sách.
  - `getItem(index)`: lấy một đối tượng SVGLength tại chỉ số cụ thể.
  - `initialize(newItem)`: khởi tạo danh sách với một đối tượng SVGLength mới.
  - `removeItem(index)`: xóa một phần tử tại chỉ số cụ thể.
  - `replaceItem(newItem, index)`: thay thế một phần tử tại chỉ số cụ thể bằng một đối tượng SVGLength mới.

## Ví dụ
Dưới đây là một số ví dụ đơn giản về cách sử dụng SVGLengthList trong JavaScript:

### Ví dụ 1: Khởi tạo và thêm chiều dài
```javascript
const svgElement = document.getElementById('mySVGElement');
const lengthList = svgElement.strokeDasharray.baseVal;

lengthList.appendItem(svgElement.ownerSVGElement.createSVGLength().setValueInUnits(SVGLength.SVG_LENGTHTYPE_PX, 50));
console.log(lengthList.numberOfItems); // Kết quả: 1
```

### Ví dụ 2: Lấy chiều dài tại chỉ số
```javascript
const firstLength = lengthList.getItem(0);
console.log(firstLength.value); // Kết quả: 50
```

### Ví dụ 3: Xóa chiều dài
```javascript
lengthList.removeItem(0);
console.log(lengthList.numberOfItems); // Kết quả: 0
```

## Giải thích
Khi làm việc với SVGLengthList, có một số điểm cần lưu ý:
- Đảm bảo rằng bạn đang làm việc với các đối tượng SVG hợp lệ để tránh lỗi.
- `numberOfItems` sẽ không tự động cập nhật cho đến khi bạn gọi các phương thức thay đổi danh sách.
- Các đơn vị chiều dài phải được chỉ định chính xác để tránh các lỗi không mong muốn.

## Tóm tắt ngắn gọn
SVGLengthList là một đối tượng trong JavaScript cho phép quản lý một danh sách các chiều dài SVG, hỗ trợ nhiều thao tác như thêm, xóa và truy xuất các giá trị chiều dài.