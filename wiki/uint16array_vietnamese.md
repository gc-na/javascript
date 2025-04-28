<!--
Meta Description: # Uint16Array trong JavaScript: Mảng 16-bit không dấu ## Tóm tắt `Uint16Array` là một kiểu mảng trong JavaScript dùng để lưu trữ các số nguyên không d...
Meta Keywords: uint16array, mảng, một, các, trong
-->

# Uint16Array trong JavaScript: Mảng 16-bit không dấu

## Tóm tắt
`Uint16Array` là một kiểu mảng trong JavaScript dùng để lưu trữ các số nguyên không dấu 16-bit, cho phép xử lý dữ liệu nhị phân một cách hiệu quả.

## Tài liệu
`Uint16Array` là một phần của `TypedArray` trong JavaScript, cho phép lưu trữ và thao tác với các số nguyên không dấu (từ 0 đến 65535) với kích thước mỗi phần tử là 16 bit. Nó rất hữu ích khi làm việc với dữ liệu nhị phân, chẳng hạn như trong âm thanh, hình ảnh, hoặc các ứng dụng yêu cầu hiệu suất cao.

### Cú pháp
```javascript
let myArray = new Uint16Array(length);
let myArrayWithValues = new Uint16Array(array);
```

### Tham số
- `length`: Số lượng phần tử trong mảng.
- `array`: Một mảng hoặc một đối tượng tương tự mảng để khởi tạo `Uint16Array`.

### Các phương thức chính
- `set()`: Thiết lập các giá trị trong mảng.
- `subarray()`: Trả về một mảng con của `Uint16Array`.
- `slice()`: Tạo một bản sao của một phần của mảng.

## Ví dụ
### Khởi tạo `Uint16Array`
```javascript
// Khởi tạo một mảng Uint16Array với 5 phần tử
let numbers = new Uint16Array(5);
console.log(numbers); // [0, 0, 0, 0, 0]
```

### Khởi tạo từ mảng
```javascript
// Khởi tạo từ một mảng thông thường
let array = [1, 2, 3, 65536]; // Lưu ý: 65536 sẽ bị cắt xuống 0
let uint16Array = new Uint16Array(array);
console.log(uint16Array); // [1, 2, 3, 0]
```

### Sử dụng phương thức `set()`
```javascript
let array1 = new Uint16Array(3);
array1.set([1000, 2000, 3000]);
console.log(array1); // [1000, 2000, 3000]
```

### Sử dụng `subarray()`
```javascript
let array2 = new Uint16Array([10, 20, 30, 40, 50]);
let subArray = array2.subarray(1, 4);
console.log(subArray); // [20, 30, 40]
```

## Giải thích
Khi sử dụng `Uint16Array`, hãy lưu ý rằng:
- Các giá trị lớn hơn 65535 sẽ tự động bị cắt xuống 0 hoặc giá trị trong khoảng 0 - 65535.
- `Uint16Array` không hỗ trợ các phép toán số học trực tiếp như các mảng thông thường. Để thực hiện các phép toán, bạn cần lặp qua từng phần tử.
- `TypedArray` không thể chứa giá trị `undefined` hoặc `NaN`.

## Tóm tắt một dòng
`Uint16Array` là một kiểu mảng trong JavaScript cho phép lưu trữ và thao tác với các số nguyên không dấu 16-bit, rất hữu ích trong các ứng dụng xử lý dữ liệu nhị phân.