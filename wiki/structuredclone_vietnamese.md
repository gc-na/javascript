<!--
Meta Description: # Tìm Hiểu Về `structuredClone` Trong JavaScript ## Tóm Tắt `structuredClone` là một phương thức trong JavaScript cho phép sao chép một đối tượng hoặc...
Meta Keywords: sao, một, chép, các, structuredclone
-->

# Tìm Hiểu Về `structuredClone` Trong JavaScript

## Tóm Tắt
`structuredClone` là một phương thức trong JavaScript cho phép sao chép một đối tượng hoặc giá trị phức tạp một cách sâu sắc, bao gồm cả các đối tượng con và các kiểu dữ liệu không thể sao chép bằng các phương pháp thông thường như `Object.assign` hoặc `JSON.stringify`.

## Tài Liệu
### Mục Đích
Phương thức `structuredClone` được thiết kế để tạo ra một bản sao sâu của một giá trị, giúp người dùng dễ dàng sao chép các cấu trúc dữ liệu phức tạp mà không lo ngại về các vấn đề như tham chiếu đối tượng hay các kiểu dữ liệu không thể sao chép.

### Cách Sử Dụng
Cú pháp cơ bản của phương thức này như sau:
```javascript
let clonedValue = structuredClone(value);
```
- `value`: Giá trị hoặc đối tượng mà bạn muốn sao chép.
- `clonedValue`: Giá trị mới được tạo ra từ bản sao của `value`.

### Chi Tiết
- `structuredClone` có thể sao chép hầu hết các kiểu dữ liệu, bao gồm đối tượng, mảng, Date, Map, Set, và các kiểu dữ liệu khác.
- Tuy nhiên, phương thức này không hỗ trợ một số kiểu dữ liệu như `Function`, `WeakMap`, `WeakSet`, `Symbol`, và `BigInt`.
- `structuredClone` có thể xử lý các đối tượng phức tạp như các đối tượng lồng nhau mà không làm thay đổi giá trị gốc.

## Ví Dụ
### Ví Dụ Cơ Bản
```javascript
const original = {
    name: "John",
    age: 30,
    address: {
        city: "Hanoi",
        country: "Vietnam"
    }
};

const cloned = structuredClone(original);
cloned.address.city = "Ho Chi Minh";

console.log(original.address.city); // "Hanoi"
console.log(cloned.address.city); // "Ho Chi Minh"
```
### Ví Dụ Với Mảng
```javascript
const originalArray = [1, 2, 3, { a: 4 }];
const clonedArray = structuredClone(originalArray);
clonedArray[3].a = 5;

console.log(originalArray[3].a); // 4
console.log(clonedArray[3].a); // 5
```

## Giải Thích
### Những Vấn Đề Thường Gặp
- **Không sao chép được một số kiểu dữ liệu**: Như đã đề cập, `structuredClone` không thể sao chép các đối tượng như `Function`, `WeakMap`, và `WeakSet`. Điều này có thể gây ra sự nhầm lẫn nếu bạn không kiểm tra kiểu dữ liệu trước khi sao chép.
- **Sao chép tuần hoàn**: Nếu bạn cố gắng sao chép một đối tượng có mối quan hệ tuần hoàn (ví dụ: một đối tượng tham chiếu đến chính nó), `structuredClone` sẽ ném ra một lỗi.
- **Hiệu suất**: Mặc dù `structuredClone` có thể hữu ích trong nhiều trường hợp, nhưng nó có thể tiêu tốn nhiều tài nguyên hơn so với các phương pháp sao chép đơn giản như `Object.assign`.

## Tóm Tắt Một Dòng
`structuredClone` trong JavaScript là một phương thức mạnh mẽ để sao chép một cách sâu sắc các giá trị và đối tượng phức tạp mà không làm thay đổi giá trị gốc.