<!--
Meta Description: # IDBCursor trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ Cụ Thể ## Tóm tắt IDBCursor là một đối tượng trong API IndexedDB của JavaScript, cho phép lậ...
Meta Keywords: bản, ghi, cursor, một, idbcursor
-->

# IDBCursor trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ Cụ Thể

## Tóm tắt
IDBCursor là một đối tượng trong API IndexedDB của JavaScript, cho phép lập trình viên duyệt qua các bản ghi trong một cửa hàng dữ liệu (object store) một cách tuần tự.

## Tài liệu
### Mục đích
IDBCursor được sử dụng để truy cập và thao tác với các bản ghi trong IndexedDB. Nó cho phép bạn duyệt qua các bản ghi theo thứ tự, thực hiện các thao tác trên từng bản ghi mà không cần phải truy vấn lại cơ sở dữ liệu cho mỗi lần.

### Cách sử dụng
IDBCursor thường được tạo ra từ một phương thức như `openCursor` hoặc `openKeyCursor` trên một đối tượng `IDBObjectStore` hoặc `IDBIndex`. Dưới đây là cú pháp cơ bản để tạo một IDBCursor:

```javascript
let request = objectStore.openCursor();
request.onsuccess = function(event) {
    let cursor = event.target.result;
    if (cursor) {
        console.log(cursor.value);
        cursor.continue();
    } else {
        console.log("Đã duyệt qua tất cả bản ghi.");
    }
};
```

### Chi tiết
- **Phương thức**: `openCursor` và `openKeyCursor` là hai phương thức chính để tạo một IDBCursor.
- **Thuộc tính**: Các thuộc tính của IDBCursor bao gồm `value` (giá trị của bản ghi hiện tại) và `key` (khóa của bản ghi).
- **Phương thức**: `continue()` và `continue(key)` cho phép bạn di chuyển đến bản ghi tiếp theo hoặc đến một bản ghi cụ thể.

## Ví dụ
### Ví dụ 1: Duyệt qua tất cả bản ghi
```javascript
let db; // Giả sử db là một kết nối đến cơ sở dữ liệu IndexedDB
let transaction = db.transaction("storeName", "readonly");
let objectStore = transaction.objectStore("storeName");

let request = objectStore.openCursor();
request.onsuccess = function(event) {
    let cursor = event.target.result;
    if (cursor) {
        console.log("Bản ghi:", cursor.value);
        cursor.continue();
    } else {
        console.log("Đã hoàn thành duyệt.");
    }
};
```

### Ví dụ 2: Duyệt qua bản ghi với điều kiện
```javascript
let request = objectStore.openCursor(IDBKeyRange.lowerBound(10));
request.onsuccess = function(event) {
    let cursor = event.target.result;
    if (cursor) {
        console.log("Bản ghi lớn hơn hoặc bằng 10:", cursor.value);
        cursor.continue();
    } else {
        console.log("Không còn bản ghi nào thỏa mãn.");
    }
};
```

## Giải thích
- **Lỗi phổ biến**: Một trong những lỗi phổ biến là quên gọi `continue()` sau khi xử lý bản ghi, dẫn đến việc không duyệt qua tất cả các bản ghi.
- **Giới hạn**: IDBCursor chỉ có thể di chuyển theo hướng tiến. Nếu bạn cần duyệt ngược, bạn sẽ cần phải mở lại cursor từ đầu.
- **Thời gian thực hiện**: Việc sử dụng IDBCursor có thể chậm hơn so với các truy vấn trực tiếp nếu có nhiều bản ghi. Do đó, hãy xem xét số lượng bản ghi khi sử dụng IDBCursor.

## Tóm tắt một dòng
IDBCursor trong JavaScript là công cụ mạnh mẽ cho phép lập trình viên duyệt qua các bản ghi trong IndexedDB một cách tuần tự và hiệu quả.