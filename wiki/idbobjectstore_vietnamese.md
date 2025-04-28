<!--
Meta Description: # IDBObjectStore trong JavaScript: Tìm Hiểu và Sử Dụng ## Tóm tắt IDBObjectStore là một thành phần quan trọng trong API IndexedDB của JavaScript, cho ...
Meta Keywords: let, liệu, idbobjectstore, dụng, một
-->

# IDBObjectStore trong JavaScript: Tìm Hiểu và Sử Dụng

## Tóm tắt
IDBObjectStore là một thành phần quan trọng trong API IndexedDB của JavaScript, cho phép lưu trữ và truy xuất các đối tượng JavaScript có cấu trúc phức tạp một cách hiệu quả trong trình duyệt.

## Tài liệu
### Mục đích
IDBObjectStore được sử dụng để lưu trữ dữ liệu kiểu đối tượng trong cơ sở dữ liệu IndexedDB. Nó cho phép bạn thực hiện các thao tác như thêm, sửa, xóa và truy vấn dữ liệu một cách dễ dàng.

### Cách sử dụng
Để sử dụng IDBObjectStore, trước tiên bạn cần mở một kết nối đến cơ sở dữ liệu IndexedDB và tạo một `transaction`. Sau đó, bạn có thể truy cập IDBObjectStore bằng cách sử dụng tên của nó.

**Cú pháp cơ bản:**
```javascript
let request = indexedDB.open("myDatabase", 1);

request.onupgradeneeded = function(event) {
    let db = event.target.result;
    let objectStore = db.createObjectStore("myObjectStore", { keyPath: "id" });
};

request.onsuccess = function(event) {
    let db = event.target.result;
    let transaction = db.transaction("myObjectStore", "readwrite");
    let objectStore = transaction.objectStore("myObjectStore");
};
```

### Chi tiết
- **Tạo Object Store:** Sử dụng phương thức `createObjectStore` trong sự kiện `onupgradeneeded`.
- **Thêm Dữ Liệu:** Sử dụng phương thức `add()` của IDBObjectStore để thêm đối tượng vào cơ sở dữ liệu.
- **Truy vấn Dữ Liệu:** Sử dụng các phương thức như `get()`, `getAll()`, hoặc `openCursor()` để truy vấn dữ liệu.
- **Xóa và Cập nhật:** Sử dụng `delete()` để xóa và `put()` để cập nhật đối tượng.

## Ví dụ
### Thêm một đối tượng vào IDBObjectStore
```javascript
let transaction = db.transaction("myObjectStore", "readwrite");
let objectStore = transaction.objectStore("myObjectStore");

let data = { id: 1, name: "John Doe", age: 30 };
let request = objectStore.add(data);

request.onsuccess = function(event) {
    console.log("Đối tượng đã được thêm thành công!");
};
```

### Lấy một đối tượng từ IDBObjectStore
```javascript
let transaction = db.transaction("myObjectStore", "readonly");
let objectStore = transaction.objectStore("myObjectStore");

let request = objectStore.get(1);

request.onsuccess = function(event) {
    console.log("Đối tượng lấy được:", event.target.result);
};
```

## Giải thích
- **Thời gian chờ:** Các thao tác với IDBObjectStore có thể không hoàn thành ngay lập tức do tính chất bất đồng bộ của IndexedDB. Hãy chắc chắn sử dụng các callback như `onsuccess` và `onerror` để xử lý kết quả.
- **Quản lý phiên giao dịch:** Hãy đảm bảo rằng phiên giao dịch đã được hoàn tất trước khi thực hiện các thao tác truy vấn hoặc thay đổi dữ liệu.

## Tóm tắt một dòng
IDBObjectStore là một phần của API IndexedDB trong JavaScript, cho phép bạn lưu trữ và quản lý dữ liệu đối tượng một cách hiệu quả trong trình duyệt.