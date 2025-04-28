<!--
Meta Description: # DOMPointReadOnly: Lớp Đọc Chỉ Trong JavaScript ## Tóm tắt DOMPointReadOnly là một lớp trong JavaScript, thuộc về API DOM (Document Object Model), đư...
Meta Keywords: tọa, một, không, trong, đổi
-->

# DOMPointReadOnly: Lớp Đọc Chỉ Trong JavaScript

## Tóm tắt
DOMPointReadOnly là một lớp trong JavaScript, thuộc về API DOM (Document Object Model), được sử dụng để đại diện cho một điểm trong không gian 2D hoặc 3D mà không cho phép thay đổi các thuộc tính của nó.

## Tài liệu
### Mục đích
DOMPointReadOnly cung cấp một cách để mô tả một điểm trong không gian 2D hoặc 3D, với các thuộc tính x, y, z và w. Lớp này rất hữu ích trong các ứng dụng đồ họa và tương tác với Canvas hoặc WebGL, nơi mà các phép toán hình học thường được thực hiện.

### Cách sử dụng
Để tạo một đối tượng DOMPointReadOnly, bạn cần tạo một đối tượng DOMPoint và sau đó sử dụng phương thức `toJSON()` để chuyển đổi nó thành đối tượng không thể thay đổi. Ví dụ:

```javascript
const point = new DOMPoint(10, 20, 30, 1);
const readOnlyPoint = Object.freeze(point.toJSON());
```

### Chi tiết
- **Thuộc tính**:
  - `x`: Giá trị tọa độ x.
  - `y`: Giá trị tọa độ y.
  - `z`: Giá trị tọa độ z (mặc định là 0 trong không gian 2D).
  - `w`: Giá trị chiều sâu (mặc định là 1).
  
- **Phương thức**:
  - `toJSON()`: Chuyển đổi đối tượng DOMPoint thành đối tượng JSON.

## Ví dụ
### Ví dụ cơ bản
```javascript
const point2D = new DOMPoint(5, 10);
console.log(`Tọa độ x: ${point2D.x}, Tọa độ y: ${point2D.y}`); // Tọa độ x: 5, Tọa độ y: 10

const point3D = new DOMPoint(5, 10, 15);
console.log(`Tọa độ x: ${point3D.x}, Tọa độ y: ${point3D.y}, Tọa độ z: ${point3D.z}`); // Tọa độ x: 5, Tọa độ y: 10, Tọa độ z: 15
```

### Chuyển đổi sang JSON
```javascript
const point = new DOMPoint(1, 2, 3, 4);
const readOnlyPoint = point.toJSON();
console.log(readOnlyPoint); // { x: 1, y: 2, z: 3, w: 4 }
```

## Giải thích
- **Cách sử dụng không chính xác**: Một số lập trình viên có thể nhầm lẫn giữa DOMPoint và DOMPointReadOnly. DOMPointReadOnly không thể được thay đổi sau khi được tạo ra, trong khi DOMPoint có thể được thay đổi.
- **Chuyển đổi giữa 2D và 3D**: Khi làm việc với DOMPoint, cần lưu ý rằng các điểm 2D sẽ có giá trị z mặc định là 0 và w mặc định là 1. Điều này có thể gây nhầm lẫn nếu không được hiểu rõ.

## Tóm tắt một dòng
DOMPointReadOnly trong JavaScript cung cấp một cách để đại diện cho một điểm trong không gian mà không cho phép thay đổi, rất hữu ích cho các ứng dụng đồ họa.