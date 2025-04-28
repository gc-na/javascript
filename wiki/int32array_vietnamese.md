<!--
Meta Description: # Int32Array trong JavaScript: Mảng Số Nguyên 32-Bit ## Tóm tắt `Int32Array` là một kiểu mảng trong JavaScript cho phép lưu trữ và thao tác với các số...
Meta Keywords: int32array, mảng, một, các, trong
-->

# Int32Array trong JavaScript: Mảng Số Nguyên 32-Bit

## Tóm tắt
`Int32Array` là một kiểu mảng trong JavaScript cho phép lưu trữ và thao tác với các số nguyên 32-bit có dấu. Nó thuộc về loại mảng kiểu nhị phân (Typed Arrays), giúp tối ưu hóa hiệu suất khi làm việc với dữ liệu nhị phân.

## Tài liệu
`Int32Array` là một phần của API mảng kiểu nhị phân trong JavaScript. Kiểu mảng này cho phép bạn tạo ra các mảng chỉ chứa các số nguyên 32-bit, với kích thước cố định, giúp tiết kiệm bộ nhớ và tăng tốc độ xử lý khi làm việc với lượng lớn dữ liệu số.

### Cú pháp
```javascript
let intArray = new Int32Array(length);
let intArrayFromArray = new Int32Array(array);
let intArrayFromBuffer = new Int32Array(buffer, byteOffset, length);
```

### Tham số
- `length`: Số nguyên xác định số phần tử trong mảng.
- `array`: Một mảng hoặc một đối tượng giống mảng mà bạn muốn chuyển đổi thành `Int32Array`.
- `buffer`: Một `ArrayBuffer` chứa dữ liệu.
- `byteOffset`: Vị trí bắt đầu trong `ArrayBuffer` để bắt đầu đọc dữ liệu.
- `length`: Số nguyên xác định số phần tử sẽ được đọc từ `ArrayBuffer`.

### Tính năng
- Hỗ trợ các phép toán mảng như `map`, `filter`, và `reduce`.
- Cung cấp các phương thức như `set` để thiết lập giá trị cho các phần tử trong mảng.
- Có thể chuyển đổi sang các kiểu mảng khác như `Array` thông qua phương thức `slice`.

## Ví dụ
### Tạo một Int32Array
```javascript
let intArray = new Int32Array(5);
console.log(intArray); // Int32Array(5) [0, 0, 0, 0, 0]
```

### Khởi tạo từ một mảng
```javascript
let numbers = [1, 2, 3, 4, 5];
let intArrayFromArray = new Int32Array(numbers);
console.log(intArrayFromArray); // Int32Array(5) [1, 2, 3, 4, 5]
```

### Khởi tạo từ một ArrayBuffer
```javascript
let buffer = new ArrayBuffer(16); // 16 bytes
let intArrayFromBuffer = new Int32Array(buffer);
console.log(intArrayFromBuffer); // Int32Array(4) [0, 0, 0, 0]
```

## Giải thích
Khi làm việc với `Int32Array`, có một số điều cần lưu ý:
- Các phần tử trong `Int32Array` chỉ có thể lưu trữ các giá trị số nguyên 32-bit có dấu, nếu bạn cố gắng lưu trữ các giá trị khác, chúng sẽ được chuyển đổi sang kiểu dữ liệu tương ứng.
- Kích thước của `Int32Array` là cố định sau khi đã được khởi tạo; bạn không thể thay đổi số lượng phần tử.
- Nếu bạn khởi tạo một `Int32Array` từ một mảng có các giá trị không phải số, những giá trị này sẽ được chuyển đổi thành số (nếu có thể).

## Tóm tắt một dòng
`Int32Array` là kiểu mảng trong JavaScript cho phép lưu trữ và thao tác với các số nguyên 32-bit có dấu, giúp tối ưu hiệu suất khi xử lý dữ liệu số lớn.