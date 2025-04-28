<!--
Meta Description: # WeakRef trong JavaScript: Khám Phá và Ứng Dụng ## Tóm tắt WeakRef là một đối tượng trong JavaScript cho phép tham chiếu đến một đối tượng mà không n...
Meta Keywords: weakref, đối, tượng, tham, chiếu
-->

# WeakRef trong JavaScript: Khám Phá và Ứng Dụng

## Tóm tắt
WeakRef là một đối tượng trong JavaScript cho phép tham chiếu đến một đối tượng mà không ngăn cản việc thu dọn bộ nhớ (garbage collection). Điều này đặc biệt hữu ích trong các tình huống mà bạn muốn giữ tham chiếu đến một đối tượng mà không ảnh hưởng đến vòng đời của nó.

## Tài liệu
### Mục đích
WeakRef được giới thiệu trong ECMAScript 2021 để giúp quản lý bộ nhớ hiệu quả hơn. Nó cho phép tạo ra một tham chiếu yếu đến một đối tượng, nghĩa là nếu không còn tham chiếu nào mạnh mẽ đến đối tượng đó, nó có thể bị thu dọn bộ nhớ.

### Cách sử dụng
Để tạo một WeakRef, bạn sử dụng cú pháp sau:

```javascript
const weakref = new WeakRef(object);
```

- `object`: Đối tượng mà bạn muốn tham chiếu yếu.

Để lấy lại đối tượng từ WeakRef, bạn có thể sử dụng phương thức `deref()`:

```javascript
const obj = weakref.deref();
```

Nếu đối tượng đã bị thu dọn, `deref()` sẽ trả về `undefined`.

### Chi tiết
- WeakRef chỉ có thể tham chiếu đến các đối tượng, không thể tham chiếu đến các kiểu dữ liệu nguyên thủy như số, chuỗi, hay boolean.
- Tham chiếu yếu không ngăn cản đối tượng bị thu dọn, điều này giúp giảm thiểu rò rỉ bộ nhớ trong các ứng dụng phức tạp.
- WeakRef không có các phương thức hay thuộc tính khác ngoài `deref()`.

## Ví dụ
### Ví dụ cơ bản
```javascript
let obj = { name: 'John' };
let weakref = new WeakRef(obj);

// Lấy lại đối tượng
let derefObj = weakref.deref();
console.log(derefObj.name); // 'John'

// Xóa tham chiếu mạnh
obj = null;

// Kiểm tra lại
derefObj = weakref.deref();
console.log(derefObj); // undefined
```

### Ví dụ sử dụng trong thực tế
```javascript
const cache = new WeakMap();

function cacheValue(key, value) {
    cache.set(key, new WeakRef(value));
}

let myObject = { data: 'Some data' };
cacheValue(myObject, myObject);

// Xóa tham chiếu mạnh
myObject = null;

// Kiểm tra cache
console.log(cache.get(myObject)?.deref()); // undefined
```

## Giải thích
- **Lưu ý**: WeakRef không đảm bảo rằng đối tượng sẽ tồn tại khi bạn gọi `deref()`. Nếu đối tượng đã bị thu dọn, bạn sẽ nhận được `undefined`.
- **Nguy cơ**: Khi sử dụng WeakRef, bạn cần cẩn thận để không tạo ra các rò rỉ bộ nhớ khác, chẳng hạn như tham chiếu mạnh đến đối tượng từ một nơi khác.
- **Chú ý**: WeakRef không hỗ trợ các cấu trúc dữ liệu như mảng hay đối tượng, chỉ có thể dùng cho các đối tượng.

## Tóm tắt ngắn gọn
WeakRef cho phép tạo ra các tham chiếu yếu đến đối tượng trong JavaScript, giúp quản lý bộ nhớ hiệu quả hơn mà không ngăn cản thu dọn bộ nhớ.