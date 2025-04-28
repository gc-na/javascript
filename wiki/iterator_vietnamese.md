<!--
Meta Description: # Iterator trong JavaScript: Khám Phá và Ứng Dụng ## Tóm tắt Iterator là một khái niệm quan trọng trong JavaScript, cho phép duyệt qua các cấu trúc dữ...
Meta Keywords: iterator, một, value, done, next
-->

# Iterator trong JavaScript: Khám Phá và Ứng Dụng

## Tóm tắt
Iterator là một khái niệm quan trọng trong JavaScript, cho phép duyệt qua các cấu trúc dữ liệu như mảng, đối tượng, và chuỗi một cách tuần tự mà không cần biết cách mà chúng được lưu trữ.

## Tài liệu
### Mục đích
Iterator là một đối tượng cung cấp phương thức để truy cập các phần tử của một cấu trúc dữ liệu mà không cần tiết lộ cấu trúc dữ liệu đó. Nó giúp cho việc lặp qua các phần tử trở nên dễ dàng và linh hoạt hơn.

### Cách sử dụng
Trong JavaScript, một iterator thực hiện hai phương thức chính:
- `next()`: Trả về đối tượng có thuộc tính `value` (giá trị hiện tại) và `done` (trạng thái hoàn tất).
- `Symbol.iterator`: Một phương thức cho phép bạn tạo ra iterator cho một đối tượng.

### Chi tiết
Mỗi iterator trong JavaScript sẽ trả về một đối tượng chứa hai thuộc tính:
- `value`: Giá trị của phần tử hiện tại.
- `done`: Một boolean cho biết liệu iterator đã hoàn thành việc duyệt hay chưa.

Ví dụ, mảng trong JavaScript đã hỗ trợ iterator. Bạn có thể sử dụng vòng lặp `for...of` để duyệt qua các phần tử của mảng mà không cần phải sử dụng chỉ số.

## Ví dụ
### Ví dụ cơ bản về Iterator với mảng
```javascript
const arr = [1, 2, 3];
const iterator = arr[Symbol.iterator]();

console.log(iterator.next()); // { value: 1, done: false }
console.log(iterator.next()); // { value: 2, done: false }
console.log(iterator.next()); // { value: 3, done: false }
console.log(iterator.next()); // { value: undefined, done: true }
```

### Ví dụ tạo Iterator tùy chỉnh
```javascript
function createIterator(items) {
    let index = 0;
    return {
        next: function() {
            if (index < items.length) {
                return { value: items[index++], done: false };
            }
            return { value: undefined, done: true };
        }
    };
}

const myIterator = createIterator(['a', 'b', 'c']);
console.log(myIterator.next()); // { value: 'a', done: false }
console.log(myIterator.next()); // { value: 'b', done: false }
console.log(myIterator.next()); // { value: 'c', done: false }
console.log(myIterator.next()); // { value: undefined, done: true }
```

## Giải thích
Khi làm việc với iterators, một số điểm cần lưu ý bao gồm:
- Đảm bảo rằng bạn không truy cập phần tử ngoài phạm vi của iterator để tránh lỗi không mong muốn.
- Các iterator chỉ có thể được sử dụng một lần. Sau khi hoàn thành, bạn cần tạo một iterator mới nếu muốn duyệt lại các phần tử.
- Sử dụng `for...of` là cách đơn giản để duyệt qua iterator mà không cần phải xử lý `next()` thủ công.

## Tóm tắt một dòng
Iterator trong JavaScript cho phép bạn duyệt qua các cấu trúc dữ liệu một cách linh hoạt và hiệu quả mà không cần biết chi tiết cụ thể của chúng.