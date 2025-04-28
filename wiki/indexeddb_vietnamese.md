<!--
Meta Description: # IndexedDB trong JavaScript: Lưu trữ dữ liệu trên trình duyệt ## Tóm tắt IndexedDB là một API trong JavaScript cho phép lưu trữ dữ liệu có cấu trúc l...
Meta Keywords: liệu, indexeddb, các, một, lưu
-->

# IndexedDB trong JavaScript: Lưu trữ dữ liệu trên trình duyệt

## Tóm tắt
IndexedDB là một API trong JavaScript cho phép lưu trữ dữ liệu có cấu trúc lớn hơn, có thể truy vấn và tìm kiếm hiệu quả, trên trình duyệt. Nó là giải pháp lý tưởng cho các ứng dụng web cần lưu trữ dữ liệu offline hoặc quản lý lượng lớn dữ liệu.

## Tài liệu

### Mục đích
IndexedDB cho phép các ứng dụng web lưu trữ dữ liệu trong trình duyệt, cung cấp khả năng lưu trữ dữ liệu kiểu key-value và hỗ trợ các kiểu dữ liệu phức tạp như object, array, và blob.

### Cách sử dụng
Để sử dụng IndexedDB, bạn cần thực hiện các bước sau:

1. **Mở hoặc tạo cơ sở dữ liệu**:
   Sử dụng `indexedDB.open()` để mở hoặc tạo cơ sở dữ liệu mới.

2. **Tạo Object Store**:
   Trong hàm `onupgradeneeded`, bạn có thể tạo các object store để lưu trữ dữ liệu.

3. **Thêm, sửa, hoặc xóa dữ liệu**:
   Sử dụng các phương thức như `add()`, `put()`, và `delete()` để quản lý dữ liệu trong object store.

4. **Truy vấn dữ liệu**:
   Sử dụng `get()`, `getAll()` hoặc cursor để truy vấn và duyệt qua dữ liệu.

### Chi tiết
Dưới đây là các phương thức chính của IndexedDB:

- **indexedDB.open()**: Mở hoặc tạo một cơ sở dữ liệu.
- **transaction()**: Tạo một giao dịch để thực hiện các thao tác với object store.
- **objectStore.add()**: Thêm một mục mới vào object store.
- **objectStore.put()**: Cập nhật một mục đã tồn tại.
- **objectStore.get()**: Lấy một mục từ object store bằng khóa.

## Ví dụ

```javascript
// Mở cơ sở dữ liệu
let request = indexedDB.open("myDatabase", 1);

request.onupgradeneeded = function(event) {
    let db = event.target.result;

    // Tạo object store
    let objectStore = db.createObjectStore("myStore", { keyPath: "id" });
};

request.onsuccess = function(event) {
    let db = event.target.result;

    // Thêm dữ liệu
    let transaction = db.transaction("myStore", "readwrite");
    let objectStore = transaction.objectStore("myStore");
    let data = { id: 1, name: "John Doe" };
    
    let addRequest = objectStore.add(data);
    
    addRequest.onsuccess = function() {
        console.log("Dữ liệu đã được thêm thành công!");
    };
};

request.onerror = function(event) {
    console.error("Lỗi mở cơ sở dữ liệu", event);
};
```

## Giải thích
Khi làm việc với IndexedDB, có một số điểm cần lưu ý:

- **Asynchronous Nature**: Tất cả các thao tác với IndexedDB là bất đồng bộ. Hãy chắc chắn rằng bạn xử lý các sự kiện như `onsuccess` và `onerror` một cách chính xác.
- **Cập nhật phiên bản**: Khi bạn thay đổi cấu trúc cơ sở dữ liệu, hãy nhớ cập nhật phiên bản để bật sự kiện `onupgradeneeded`.
- **Chạy trên HTTPS**: IndexedDB chỉ hoạt động trên các trang web được phục vụ qua HTTPS hoặc trên localhost.

## Tóm tắt một dòng
IndexedDB là một API mạnh mẽ cho phép lưu trữ và truy vấn dữ liệu lớn trong trình duyệt, hỗ trợ các ứng dụng web hoạt động offline.