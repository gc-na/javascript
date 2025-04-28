<!--
Meta Description: # WeakSet trong JavaScript: Hướng dẫn chi tiết và ví dụ ## Tóm tắt WeakSet là một cấu trúc dữ liệu trong JavaScript cho phép lưu trữ các đối tượng mà ...
Meta Keywords: weakset, không, đối, tượng, một
-->

# WeakSet trong JavaScript: Hướng dẫn chi tiết và ví dụ

## Tóm tắt
WeakSet là một cấu trúc dữ liệu trong JavaScript cho phép lưu trữ các đối tượng mà không giữ tham chiếu mạnh đến chúng, giúp quản lý bộ nhớ tốt hơn trong các ứng dụng.

## Tài liệu
### Mục đích
WeakSet được thiết kế để lưu trữ các đối tượng mà không giữ tham chiếu mạnh, có nghĩa là nếu không còn tham chiếu nào đến một đối tượng trong WeakSet, đối tượng đó có thể bị thu hồi bởi Garbage Collector. Điều này giúp giảm thiểu rò rỉ bộ nhớ trong các ứng dụng lớn.

### Cách sử dụng
Để sử dụng WeakSet, bạn cần tạo một thể hiện của nó bằng cách sử dụng từ khóa `new` như sau:

```javascript
const myWeakSet = new WeakSet();
```

WeakSet chỉ hỗ trợ các đối tượng như là phần tử. Các kiểu dữ liệu nguyên thủy như số, chuỗi, hoặc boolean không thể được thêm vào WeakSet.

### Các phương thức chính
- **add(value)**: Thêm một đối tượng vào WeakSet.
- **delete(value)**: Xóa một đối tượng khỏi WeakSet.
- **has(value)**: Kiểm tra xem một đối tượng có tồn tại trong WeakSet hay không.

## Ví dụ
### Tạo và sử dụng WeakSet

```javascript
const obj1 = {};
const obj2 = {};
const myWeakSet = new WeakSet();

myWeakSet.add(obj1);
console.log(myWeakSet.has(obj1)); // true
console.log(myWeakSet.has(obj2)); // false

myWeakSet.delete(obj1);
console.log(myWeakSet.has(obj1)); // false
```

### Quản lý bộ nhớ
```javascript
let obj3 = {};
const myWeakSet2 = new WeakSet();
myWeakSet2.add(obj3);

// Nếu obj3 không còn được tham chiếu ở đâu khác, nó sẽ bị thu hồi bởi Garbage Collector
obj3 = null; // obj3 không còn tham chiếu đến đối tượng
```

## Giải thích
### Những điều cần lưu ý
- WeakSet chỉ có thể chứa các đối tượng, không hỗ trợ kiểu dữ liệu nguyên thủy.
- Không thể lặp qua WeakSet, vì nó không có phương thức `forEach` hoặc không có khả năng truy cập bằng chỉ số.
- WeakSet không có thuộc tính `size`, điều này có nghĩa là bạn không thể biết số lượng phần tử hiện có trong WeakSet.

### Những cạm bẫy phổ biến
- Không thể thêm kiểu dữ liệu nguyên thủy vào WeakSet sẽ gây ra lỗi.
- Việc sử dụng WeakSet không phù hợp nếu bạn cần một cấu trúc dữ liệu có khả năng truy cập mạnh mẽ và lặp qua phần tử.

## Tóm tắt một câu
WeakSet trong JavaScript là một cấu trúc dữ liệu cho phép lưu trữ các đối tượng mà không giữ tham chiếu mạnh, giúp quản lý bộ nhớ hiệu quả hơn.