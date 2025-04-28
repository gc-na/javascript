<!--
Meta Description: # Tập Hợp (Set) trong JavaScript: Một Công Cụ Quản Lý Dữ Liệu Hiệu Quả ## Tóm tắt Tập hợp (Set) trong JavaScript là một đối tượng cho phép lưu trữ các...
Meta Keywords: tập, hợp, giá, trị, một
-->

# Tập Hợp (Set) trong JavaScript: Một Công Cụ Quản Lý Dữ Liệu Hiệu Quả

## Tóm tắt
Tập hợp (Set) trong JavaScript là một đối tượng cho phép lưu trữ các giá trị duy nhất, không trùng lặp. Nó cung cấp một cách hiệu quả để quản lý và thao tác với tập hợp các dữ liệu mà không cần phải lo lắng về việc có các phần tử trùng lặp.

## Tài liệu
### Mục đích
Tập hợp (Set) được sử dụng để lưu trữ các giá trị mà không cần quan tâm đến thứ tự của chúng, và mỗi giá trị chỉ xuất hiện một lần trong tập hợp. Điều này rất hữu ích trong nhiều tình huống lập trình, chẳng hạn như khi bạn cần loại bỏ các giá trị trùng lặp từ một mảng.

### Cách sử dụng
Để tạo một tập hợp (Set), bạn sử dụng cú pháp sau:

```javascript
const mySet = new Set([iterable]);
```

- `iterable`: Là một đối tượng có thể lặp (như mảng, chuỗi, hoặc bất kỳ đối tượng nào có phương thức `[Symbol.iterator]`) với các giá trị sẽ được thêm vào tập hợp.

### Các phương thức chính của Set
- **add(value)**: Thêm một giá trị vào tập hợp. Nếu giá trị đã tồn tại, nó sẽ không được thêm vào.
- **delete(value)**: Xóa một giá trị khỏi tập hợp. Trả về `true` nếu giá trị đã được xóa, ngược lại trả về `false`.
- **has(value)**: Kiểm tra xem một giá trị có tồn tại trong tập hợp hay không. Trả về `true` hoặc `false`.
- **clear()**: Xóa tất cả các giá trị trong tập hợp.
- **size**: Thuộc tính cho biết số lượng phần tử trong tập hợp.

## Ví dụ
### Tạo một tập hợp
```javascript
const fruits = new Set(['apple', 'banana', 'orange']);
console.log(fruits); // Set { 'apple', 'banana', 'orange' }
```

### Thêm giá trị
```javascript
fruits.add('mango');
console.log(fruits); // Set { 'apple', 'banana', 'orange', 'mango' }
```

### Kiểm tra sự tồn tại của giá trị
```javascript
console.log(fruits.has('banana')); // true
console.log(fruits.has('grape')); // false
```

### Xóa giá trị
```javascript
fruits.delete('banana');
console.log(fruits); // Set { 'apple', 'orange', 'mango' }
```

### Xóa tất cả giá trị
```javascript
fruits.clear();
console.log(fruits); // Set {}
```

## Giải thích
Khi làm việc với tập hợp (Set), có vài điều cần lưu ý:
- Tập hợp chỉ lưu trữ các giá trị duy nhất. Nếu bạn cố gắng thêm một giá trị đã có, nó sẽ không được thêm vào.
- Tập hợp không giữ thứ tự của các phần tử, vì vậy khi bạn duyệt qua các phần tử, thứ tự có thể không giống như khi bạn thêm chúng.
- Tập hợp không hỗ trợ các kiểu dữ liệu phức tạp như Object hoặc Array dưới dạng các phần tử duy nhất trừ khi bạn sử dụng các tham chiếu khác nhau (ví dụ: hai đối tượng khác nhau với cùng thuộc tính sẽ được coi là khác nhau).

## Tóm tắt
Tập hợp (Set) trong JavaScript là một công cụ mạnh mẽ giúp quản lý và thao tác với dữ liệu duy nhất một cách hiệu quả và đơn giản.