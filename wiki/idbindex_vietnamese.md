<!--
Meta Description: # IDBIndex trong JavaScript: Hướng Dẫn Chi Tiết ## Tóm Tắt `IDBIndex` là một đối tượng trong API IndexedDB của JavaScript, cho phép truy cập và tìm ki...
Meta Keywords: mục, chỉ, các, idbindex, trong
-->

# IDBIndex trong JavaScript: Hướng Dẫn Chi Tiết

## Tóm Tắt
`IDBIndex` là một đối tượng trong API IndexedDB của JavaScript, cho phép truy cập và tìm kiếm dữ liệu trong các chỉ mục của cơ sở dữ liệu.

## Tài Liệu
### Mục đích
`IDBIndex` được sử dụng để tạo và quản lý các chỉ mục trong IndexedDB, giúp tối ưu hóa việc truy vấn dữ liệu. Chỉ mục cho phép bạn tìm kiếm dữ liệu theo các thuộc tính cụ thể mà không cần phải quét toàn bộ bảng.

### Cách Sử Dụng
Để sử dụng `IDBIndex`, bạn cần thực hiện các bước cơ bản sau:

1. **Mở cơ sở dữ liệu**: Sử dụng `indexedDB.open()` để mở hoặc tạo một cơ sở dữ liệu.
2. **Tạo một phiên bản mới**: Sử dụng `onupgradeneeded` để tạo một phiên bản mới của cơ sở dữ liệu và chỉ mục.
3. **Lấy chỉ mục**: Sử dụng phương thức `transaction.objectStore().index()` để lấy đối tượng `IDBIndex`.
4. **Thực hiện tìm kiếm**: Sử dụng các phương thức như `get()`, `getAll()`, `count()` để thực hiện các truy vấn trên chỉ mục.

### Chi Tiết
- **Cú pháp**: 
  ```javascript
  let index = objectStore.createIndex(name, keyPath, [options]);
  ```

- **Tham số**:
  - `name`: Tên của chỉ mục.
  - `keyPath`: Thuộc tính hoặc mảng các thuộc tính của đối tượng để xây dựng chỉ mục.
  - `options`: (Tùy chọn) Một đối tượng chứa các tùy chọn như `unique` hoặc `multiEntry`.

### Phương thức chính của IDBIndex
- `get(key)`: Lấy một mục theo khóa từ chỉ mục.
- `getAll(key)`: Lấy tất cả các mục phù hợp với khóa.
- `count()`: Đếm số lượng mục trong chỉ mục.

## Ví dụ
### Tạo và Sử Dụng IDBIndex
```javascript
let request = indexedDB.open("MyDatabase", 1);

request.onupgradeneeded = function(event) {
  let db = event.target.result;
  let objectStore = db.createObjectStore("MyObjectStore", { keyPath: "id" });
  objectStore.createIndex("nameIndex", "name", { unique: false });
};

request.onsuccess = function(event) {
  let db = event.target.result;
  let transaction = db.transaction("MyObjectStore");
  let store = transaction.objectStore("MyObjectStore");
  let index = store.index("nameIndex");

  index.get("John").onsuccess = function(event) {
    console.log(event.target.result);
  };
};
```

## Giải Thích
Khi làm việc với `IDBIndex`, có một số điểm cần lưu ý:
- Chỉ mục chỉ có thể được tạo trong sự kiện `onupgradeneeded`.
- Các truy vấn trên chỉ mục có thể không trả về kết quả nếu khóa không tồn tại.
- Đảm bảo rằng tên của chỉ mục là duy nhất trong phạm vi của `objectStore`.

## Tóm Tắt Một Dòng
`IDBIndex` trong JavaScript là một công cụ mạnh mẽ để tìm kiếm và truy vấn dữ liệu trong IndexedDB thông qua các chỉ mục.