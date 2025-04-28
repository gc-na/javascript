<!--
Meta Description: # IDBKeyRange: Dải Khóa trong JavaScript cho IndexedDB ## Tóm tắt `IDBKeyRange` là một đối tượng trong JavaScript cho phép xác định các dải khóa khi t...
Meta Keywords: idbkeyrange, dải, khóa, một, các
-->

# IDBKeyRange: Dải Khóa trong JavaScript cho IndexedDB

## Tóm tắt
`IDBKeyRange` là một đối tượng trong JavaScript cho phép xác định các dải khóa khi thao tác với cơ sở dữ liệu IndexedDB. Nó hỗ trợ việc truy vấn các mục dữ liệu theo khoảng giá trị, giúp người dùng dễ dàng tìm kiếm và lọc dữ liệu.

## Tài liệu
`IDBKeyRange` được sử dụng chủ yếu trong ngữ cảnh của IndexedDB, một API cho phép lưu trữ dữ liệu lớn trong trình duyệt. Đối tượng này cho phép bạn tạo ra các dải khóa để tìm kiếm dữ liệu theo các tiêu chí nhất định, như giá trị lớn hơn, nhỏ hơn, hoặc nằm trong một khoảng giá trị cụ thể.

### Cách sử dụng
Có ba phương thức chính để tạo ra `IDBKeyRange`:
1. **`IDBKeyRange.only(value)`**: Tạo một dải khóa chỉ bao gồm giá trị cụ thể.
2. **`IDBKeyRange.lowerBound(lower, open)`**: Tạo một dải khóa với giới hạn dưới. Tham số `open` xác định xem giới hạn có bao gồm giá trị đó hay không.
3. **`IDBKeyRange.upperBound(upper, open)`**: Tương tự như trên nhưng cho giới hạn trên.
4. **`IDBKeyRange.bound(lower, upper, lowerOpen, upperOpen)`**: Tạo một dải khóa từ giá trị dưới đến giá trị trên với các tham số xác định xem các giới hạn có mở hay không.

### Ví dụ
Dưới đây là một số ví dụ cơ bản để minh họa cách sử dụng `IDBKeyRange`:

```javascript
// Tạo dải khóa chỉ với giá trị cụ thể
let keyRangeOnly = IDBKeyRange.only("exampleValue");

// Tạo dải khóa với giới hạn dưới
let keyRangeLowerBound = IDBKeyRange.lowerBound(10, true); // không bao gồm 10

// Tạo dải khóa với giới hạn trên
let keyRangeUpperBound = IDBKeyRange.upperBound(50); // bao gồm 50

// Tạo dải khóa với cả giới hạn dưới và trên
let keyRangeBound = IDBKeyRange.bound(1, 100, true, false); // không bao gồm 1, bao gồm 100
```

## Giải thích
Một số điểm cần lưu ý khi sử dụng `IDBKeyRange`:
- **Giá trị phải có thể so sánh**: Các giá trị được sử dụng trong `IDBKeyRange` cần có khả năng so sánh (như số, chuỗi, v.v.).
- **Không sử dụng với kiểu dữ liệu không hợp lệ**: Nếu bạn cố gắng sử dụng các kiểu dữ liệu không hợp lệ như đối tượng phức tạp, bạn sẽ gặp lỗi.
- **Lưu ý về các tham số mở**: Việc sử dụng các tham số `open` có thể làm thay đổi hành vi của dải khóa, vì vậy bạn nên cân nhắc kỹ khi thiết lập chúng.

## Tóm tắt một dòng
`IDBKeyRange` là một công cụ mạnh mẽ trong JavaScript cho phép xác định dải khóa khi truy vấn dữ liệu trong IndexedDB, hỗ trợ việc lọc và tìm kiếm dữ liệu một cách hiệu quả.