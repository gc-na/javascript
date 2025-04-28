<!--
Meta Description: # Map trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ ## Tóm tắt Map trong JavaScript là một cấu trúc dữ liệu cho phép lưu trữ cặp khóa-giá trị, nơi khó...
Meta Keywords: map, khóa, giá, trị, một
-->

# Map trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ

## Tóm tắt
Map trong JavaScript là một cấu trúc dữ liệu cho phép lưu trữ cặp khóa-giá trị, nơi khóa có thể là bất kỳ kiểu dữ liệu nào, khác với đối tượng (object) chỉ cho phép chuỗi hoặc symbol làm khóa.

## Tài liệu
Map là một loại cấu trúc dữ liệu trong JavaScript được giới thiệu từ ECMAScript 6 (ES6). Nó cho phép lập trình viên tạo ra các đối tượng lưu trữ dữ liệu dưới dạng cặp khóa-giá trị. Một số điểm nổi bật của Map bao gồm:

- **Khóa linh hoạt**: Khóa trong Map có thể là bất kỳ kiểu dữ liệu nào, bao gồm đối tượng, hàm, hay giá trị nguyên thủy.
- **Thứ tự duy trì**: Các phần tử trong Map được lưu trữ theo thứ tự mà chúng được thêm vào, giúp dễ dàng truy cập theo thứ tự.
- **Kích thước**: Map có thuộc tính `size` cho phép biết số lượng cặp khóa-giá trị hiện có.
- **Phương thức hữu ích**: Map cung cấp nhiều phương thức như `set()`, `get()`, `has()`, `delete()`, và `clear()` để quản lý dữ liệu một cách hiệu quả.

### Cách sử dụng
Để sử dụng Map, bạn có thể khởi tạo một đối tượng Map như sau:

```javascript
const myMap = new Map();
```

Sau đó, bạn có thể thêm cặp khóa-giá trị vào Map:

```javascript
myMap.set('key1', 'value1');
myMap.set('key2', 'value2');
```

Để lấy giá trị theo khóa, sử dụng phương thức `get()`:

```javascript
console.log(myMap.get('key1')); // Kết quả: 'value1'
```

Để kiểm tra sự tồn tại của một khóa, sử dụng `has()`:

```javascript
console.log(myMap.has('key2')); // Kết quả: true
```

Để xóa một cặp khóa-giá trị, dùng `delete()`:

```javascript
myMap.delete('key1');
```

Cuối cùng, để xóa tất cả các cặp, sử dụng `clear()`:

```javascript
myMap.clear();
```

## Ví dụ
Dưới đây là một ví dụ đầy đủ về việc sử dụng Map trong JavaScript:

```javascript
// Khởi tạo một Map mới
const fruitsMap = new Map();

// Thêm các cặp khóa-giá trị
fruitsMap.set('apple', 1);
fruitsMap.set('banana', 2);
fruitsMap.set('orange', 3);

// Lấy giá trị theo khóa
console.log(fruitsMap.get('banana')); // Kết quả: 2

// Kiểm tra sự tồn tại của một khóa
console.log(fruitsMap.has('apple')); // Kết quả: true

// Xóa một cặp khóa-giá trị
fruitsMap.delete('orange');

// Lặp qua các cặp khóa-giá trị
fruitsMap.forEach((value, key) => {
    console.log(`${key}: ${value}`);
});

// Kết quả: 
// apple: 1
// banana: 2

// Xóa tất cả các cặp
fruitsMap.clear();
console.log(fruitsMap.size); // Kết quả: 0
```

## Giải thích
Khi sử dụng Map, bạn cần lưu ý rằng:

- Các khóa trong Map là duy nhất. Nếu bạn thêm một cặp với khóa đã tồn tại, giá trị mới sẽ ghi đè lên giá trị cũ.
- Map có thể dễ dàng bị lặp qua bằng các phương thức như `forEach()` hoặc `for...of`, giúp việc xử lý dữ liệu trở nên dễ dàng hơn.
- Mặc dù Map rất mạnh mẽ, nhưng bạn cũng nên cân nhắc khi sử dụng nó so với các cấu trúc dữ liệu khác như đối tượng (object) nếu bạn chỉ cần lưu trữ các cặp khóa-giá trị đơn giản.

## Tóm tắt một dòng
Map trong JavaScript là một cấu trúc dữ liệu mạnh mẽ cho phép lưu trữ và quản lý các cặp khóa-giá trị với nhiều tính năng hữu ích.