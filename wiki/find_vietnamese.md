<!--
Meta Description: # Tìm kiếm với phương thức `find` trong JavaScript ## Tóm tắt Phương thức `find` trong JavaScript là một phương thức của mảng, cho phép bạn tìm kiếm v...
Meta Keywords: phần, find, mảng, trả, phương
-->

# Tìm kiếm với phương thức `find` trong JavaScript

## Tóm tắt
Phương thức `find` trong JavaScript là một phương thức của mảng, cho phép bạn tìm kiếm và trả về phần tử đầu tiên trong mảng thỏa mãn điều kiện đã chỉ định.

## Tài liệu
### Mục đích
Phương thức `find` được sử dụng để tìm kiếm một phần tử trong mảng dựa trên một hàm kiểm tra. Nếu có ít nhất một phần tử thỏa mãn điều kiện, phương thức sẽ trả về phần tử đó. Nếu không, nó sẽ trả về `undefined`.

### Cú pháp
```javascript
array.find(callback(element[, index[, array]])[, thisArg])
```

- **array**: Mảng mà bạn muốn tìm kiếm.
- **callback**: Hàm được gọi cho từng phần tử trong mảng. Nó nhận các tham số:
  - **element**: Phần tử hiện tại đang được duyệt.
  - **index** (tùy chọn): Chỉ số của phần tử hiện tại.
  - **array** (tùy chọn): Mảng gốc mà phương thức `find` đang được gọi.
- **thisArg** (tùy chọn): Giá trị để sử dụng làm `this` trong hàm callback.

### Chi tiết
- `find` sẽ duyệt qua từng phần tử của mảng và thực hiện hàm callback cho mỗi phần tử.
- Nếu hàm callback trả về `true` cho một phần tử, phương thức `find` sẽ trả về phần tử đó ngay lập tức.
- Nếu không tìm thấy phần tử nào thỏa mãn điều kiện, nó sẽ trả về `undefined`.

## Ví dụ
### Ví dụ cơ bản
```javascript
const numbers = [4, 9, 16, 25];

const firstEven = numbers.find(num => num % 2 === 0);
console.log(firstEven); // Kết quả: 4
```

### Ví dụ với đối tượng
```javascript
const users = [
    { id: 1, name: 'Alice' },
    { id: 2, name: 'Bob' },
    { id: 3, name: 'Charlie' }
];

const user = users.find(user => user.id === 2);
console.log(user); // Kết quả: { id: 2, name: 'Bob' }
```

## Giải thích
- Một số điểm cần lưu ý khi sử dụng `find`:
  - `find` chỉ trả về phần tử đầu tiên thỏa mãn điều kiện. Nếu bạn cần tất cả các phần tử thỏa mãn, hãy sử dụng `filter`.
  - Nếu không có phần tử nào thỏa mãn, `find` sẽ trả về `undefined`, điều này có thể gây ra lỗi nếu bạn không kiểm tra trước.
  - `find` không thay đổi mảng gốc mà chỉ trả về giá trị của phần tử tìm thấy.

## Tóm tắt một dòng
Phương thức `find` trong JavaScript giúp tìm phần tử đầu tiên trong mảng thỏa mãn điều kiện được chỉ định bởi hàm callback.