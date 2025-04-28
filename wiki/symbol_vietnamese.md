<!--
Meta Description: # Symbol trong JavaScript: Tìm Hiểu và Sử Dụng ## Tóm Tắt Symbol là một kiểu dữ liệu nguyên thủy trong JavaScript, được giới thiệu trong ECMAScript 6 ...
Meta Keywords: symbol, một, dụng, các, trong
-->

# Symbol trong JavaScript: Tìm Hiểu và Sử Dụng

## Tóm Tắt
Symbol là một kiểu dữ liệu nguyên thủy trong JavaScript, được giới thiệu trong ECMAScript 6 (ES6), cho phép tạo ra các giá trị duy nhất và không thể thay đổi, thường được dùng làm khóa cho thuộc tính của đối tượng.

## Tài Liệu
Symbol là một loại dữ liệu độc đáo trong JavaScript, được sử dụng để tạo ra các giá trị duy nhất. Mỗi khi bạn gọi hàm `Symbol()`, nó sẽ trả về một giá trị Symbol mới, không giống với bất kỳ giá trị Symbol nào khác, ngay cả khi bạn sử dụng cùng một mô tả.

### Mục Đích
- Tạo ra các khóa độc nhất cho thuộc tính đối tượng, giúp tránh xung đột giữa các thuộc tính.
- Cung cấp các biểu tượng cho các thuộc tính không thể truy cập qua vòng lặp `for...in` hoặc phương thức `Object.keys()`.

### Cách Sử Dụng
Để tạo một Symbol, bạn có thể sử dụng cú pháp sau:
```javascript
const mySymbol = Symbol('description');
```
Mô tả (description) ở đây là tùy chọn, chỉ để giúp bạn nhận diện Symbol khi cần thiết.

## Ví Dụ
### Ví dụ cơ bản
```javascript
const symbol1 = Symbol('a unique identifier');
const symbol2 = Symbol('a unique identifier');

console.log(symbol1 === symbol2); // false, vì mỗi Symbol là duy nhất

const obj = {
    [symbol1]: 'value1',
    [symbol2]: 'value2'
};

console.log(obj[symbol1]); // 'value1'
console.log(obj[symbol2]); // 'value2'
```

### Sử Dụng Symbol trong Đối Tượng
```javascript
const uniqueKey = Symbol('key');
const myObject = {
    [uniqueKey]: 'Hello World'
};

console.log(myObject[uniqueKey]); // 'Hello World'
console.log(Object.keys(myObject)); // [] (không trả về khóa Symbol)
```

## Giải Thích
Mặc dù Symbol rất hữu ích, nhưng có một số điều cần lưu ý:
- Không thể chuyển đổi Symbol thành chuỗi hoặc số, vì vậy bạn cần phải cẩn thận khi sử dụng.
- Symbol không thể được lặp qua các phương thức như `for...in` hoặc `Object.keys()`.
- Nếu bạn cần tạo ra Symbol giống nhau, bạn có thể sử dụng `Symbol.for(key)`, nơi `key` là một chuỗi. Điều này sẽ trả về Symbol đã tồn tại nếu nó đã được tạo ra trước đó.

## Tóm Tắt Một Câu
Symbol trong JavaScript là một kiểu dữ liệu nguyên thủy dùng để tạo các giá trị duy nhất cho thuộc tính đối tượng, giúp tránh xung đột trong mã nguồn.