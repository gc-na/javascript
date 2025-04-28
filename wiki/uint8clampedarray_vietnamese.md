<!--
Meta Description: # Uint8ClampedArray trong JavaScript: Mảng số nguyên 8-bit bị giới hạn ## Tóm tắt `Uint8ClampedArray` là một loại mảng trong JavaScript dùng để lưu tr...
Meta Keywords: uint8clampedarray, 255, mảng, một, giá
-->

# Uint8ClampedArray trong JavaScript: Mảng số nguyên 8-bit bị giới hạn

## Tóm tắt
`Uint8ClampedArray` là một loại mảng trong JavaScript dùng để lưu trữ các số nguyên không dấu (0 đến 255). Các giá trị bên ngoài khoảng này sẽ được "cắt" lại để nằm trong giới hạn, giúp xử lý các dữ liệu hình ảnh một cách an toàn và hiệu quả.

## Tài liệu
`Uint8ClampedArray` là một trong những kiểu mảng của `Typed Arrays` trong JavaScript. Nó cho phép bạn tạo ra một mảng có kích thước cố định, nơi mỗi phần tử là một số nguyên không dấu 8-bit (0 đến 255). Nếu bạn cố gắng gán giá trị nhỏ hơn 0, giá trị đó sẽ trở thành 0. Ngược lại, nếu bạn gán giá trị lớn hơn 255, giá trị đó sẽ trở thành 255.

### Cú pháp
```javascript
let array = new Uint8ClampedArray(length);
let array = new Uint8ClampedArray(arrayLike);
let array = new Uint8ClampedArray(buffer, byteOffset, length);
```

- `length`: Kích thước của mảng.
- `arrayLike`: Một đối tượng tương tự như mảng mà bạn muốn chuyển đổi thành `Uint8ClampedArray`.
- `buffer`: Một `ArrayBuffer` mà bạn muốn sử dụng làm nền tảng cho `Uint8ClampedArray`.
- `byteOffset`: Vị trí bắt đầu trong `buffer` để tạo mảng.
- `length`: Số lượng phần tử trong `Uint8ClampedArray` muốn tạo.

### Tính năng chính
- Các giá trị trong mảng luôn nằm trong khoảng [0, 255].
- Hữu ích cho việc xử lý hình ảnh, âm thanh, và dữ liệu nhị phân.

## Ví dụ
### Tạo một Uint8ClampedArray
```javascript
let clampedArray = new Uint8ClampedArray(5);
console.log(clampedArray); // [0, 0, 0, 0, 0]
```

### Gán giá trị
```javascript
let colors = new Uint8ClampedArray(3);
colors[0] = 256; // sẽ trở thành 255
colors[1] = -10; // sẽ trở thành 0
colors[2] = 100;

console.log(colors); // [255, 0, 100]
```

### Tạo từ một mảng
```javascript
let arr = [10, 20, 300, -5, 255];
let clampedArr = new Uint8ClampedArray(arr);

console.log(clampedArr); // [10, 20, 255, 0, 255]
```

## Giải thích
Một số vấn đề thường gặp khi sử dụng `Uint8ClampedArray` bao gồm:
- ***Giá trị không hợp lệ***: Khi gán giá trị ra ngoài khoảng [0, 255], giá trị sẽ tự động điều chỉnh về 0 hoặc 255.
- ***Hiệu suất***: Mặc dù `Typed Arrays` nhanh hơn so với mảng thông thường, nhưng bạn cần chú ý đến kích thước của mảng, đặc biệt khi xử lý dữ liệu lớn.

Để tránh lỗi, nên kiểm tra giá trị trước khi gán hoặc sử dụng các phương thức khác để xử lý dữ liệu.

## Tóm tắt một dòng
`Uint8ClampedArray` là một loại mảng trong JavaScript lưu trữ các số nguyên không dấu 8-bit và tự động cắt giá trị ngoài khoảng [0, 255].