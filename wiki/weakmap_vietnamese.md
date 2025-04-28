<!--
Meta Description: # WeakMap trong JavaScript: Tính năng và Cách sử dụng ## Tóm tắt WeakMap là một kiểu dữ liệu trong JavaScript cho phép lưu trữ các cặp khóa-giá trị mà...
Meta Keywords: weakmap, khóa, các, không, giá
-->

# WeakMap trong JavaScript: Tính năng và Cách sử dụng

## Tóm tắt
WeakMap là một kiểu dữ liệu trong JavaScript cho phép lưu trữ các cặp khóa-giá trị mà khóa là các đối tượng. Khác với Map, WeakMap không giữ mạnh các tham chiếu đến các đối tượng khóa, điều này giúp quản lý bộ nhớ hiệu quả hơn.

## Tài liệu
WeakMap là một đối tượng mà bạn có thể sử dụng để lưu trữ các cặp khóa-giá trị, trong đó khóa phải là một đối tượng và giá trị có thể là bất kỳ kiểu dữ liệu nào. WeakMap có những đặc điểm nổi bật như sau:

- **Khóa phải là đối tượng**: Các khóa trong WeakMap chỉ có thể là các đối tượng. Các kiểu dữ liệu nguyên thủy như số, chuỗi hoặc boolean không thể được sử dụng làm khóa.
- **Tham chiếu yếu**: WeakMap không giữ tham chiếu mạnh đến khóa. Nếu không còn tham chiếu nào đến khóa, Garbage Collector sẽ tự động giải phóng bộ nhớ.
- **Không thể lặp lại**: Bạn không thể lặp qua các khóa hoặc giá trị của WeakMap. Điều này giúp bảo vệ thông tin lưu trữ bên trong.

### Cú pháp
```javascript
let weakMap = new WeakMap();
```

### Các phương thức chính
- `set(key, value)`: Thêm một cặp khóa-giá trị vào WeakMap.
- `get(key)`: Trả về giá trị tương ứng với khóa nếu nó tồn tại, nếu không trả về `undefined`.
- `has(key)`: Kiểm tra xem khóa có tồn tại trong WeakMap hay không.
- `delete(key)`: Xóa cặp khóa-giá trị khỏi WeakMap.

## Ví dụ
### Ví dụ 1: Tạo và sử dụng WeakMap
```javascript
let obj1 = {};
let obj2 = {};
let weakMap = new WeakMap();

weakMap.set(obj1, "Giá trị của obj1");
weakMap.set(obj2, "Giá trị của obj2");

console.log(weakMap.get(obj1)); // "Giá trị của obj1"
console.log(weakMap.has(obj2)); // true

weakMap.delete(obj1);
console.log(weakMap.has(obj1)); // false
```

### Ví dụ 2: Quản lý bộ nhớ
```javascript
let weakMap = new WeakMap();

(function() {
    let obj = {};
    weakMap.set(obj, "Thông tin tạm thời");
})();
console.log(weakMap.has(obj)); // undefined, obj đã bị thu hồi
```

## Giải thích
Một số điểm cần lưu ý khi sử dụng WeakMap:

- **Không thể sử dụng kiểu dữ liệu nguyên thủy làm khóa**: Nếu bạn cố gắng sử dụng một chuỗi hoặc số làm khóa, sẽ xảy ra lỗi.
- **Không có phương thức lặp lại**: Do không thể lặp qua các mục trong WeakMap, bạn không thể lấy danh sách tất cả các khóa hoặc giá trị.
- **Quản lý bộ nhớ tự động**: WeakMap giúp giảm thiểu rò rỉ bộ nhớ bằng cách cho phép Garbage Collector giải phóng các đối tượng không còn cần thiết.

## Tóm tắt một dòng
WeakMap là một kiểu dữ liệu trong JavaScript cho phép lưu trữ các cặp khóa-giá trị với khóa là đối tượng và có khả năng quản lý bộ nhớ hiệu quả thông qua các tham chiếu yếu.