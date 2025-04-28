<!--
Meta Description: # IDBTransaction trong JavaScript: Hướng Dẫn Chi Tiết ## Tóm Tắt IDBTransaction là một phần của API IndexedDB trong JavaScript, cho phép thực hiện các...
Meta Keywords: giao, dịch, một, các, thực
-->

# IDBTransaction trong JavaScript: Hướng Dẫn Chi Tiết

## Tóm Tắt
IDBTransaction là một phần của API IndexedDB trong JavaScript, cho phép thực hiện các thao tác giao dịch trên cơ sở dữ liệu. Nó đảm bảo rằng các thay đổi được thực hiện một cách an toàn và nhất quán.

## Tài Liệu
### Mục Đích
IDBTransaction cho phép bạn thực hiện các thao tác trên cơ sở dữ liệu được quản lý bởi API IndexedDB. Nó hỗ trợ cho việc thực hiện các thao tác như thêm, sửa, xóa dữ liệu trong một giao dịch, đảm bảo rằng tất cả các thay đổi sẽ thành công hoặc không có thay đổi nào được thực hiện.

### Cách Sử Dụng
Để tạo một IDBTransaction, trước tiên bạn cần có một IDBDatabase. Bạn có thể tạo một giao dịch bằng cách gọi phương thức `transaction` trên đối tượng IDBDatabase. Dưới đây là cú pháp cơ bản:

```javascript
const transaction = db.transaction(storeNames, mode);
```

- **storeNames**: Một chuỗi hoặc mảng các tên của object store mà bạn muốn thao tác.
- **mode**: Chế độ giao dịch, có thể là "readonly" (chỉ đọc) hoặc "readwrite" (đọc và ghi).

### Chi Tiết
- **Phương Thức**:
  - `objectStore`: Trả về một object store từ giao dịch.
  - `abort`: Hủy bỏ giao dịch.
  - `commit`: Xác nhận giao dịch.

- **Chế Độ Giao Dịch**:
  - `readonly`: Không cho phép thay đổi dữ liệu.
  - `readwrite`: Cho phép thay đổi dữ liệu.

- **Sự Kiện**:
  - `complete`: Sự kiện xảy ra khi giao dịch hoàn tất.
  - `error`: Sự kiện xảy ra khi có lỗi trong giao dịch.
  - `abort`: Sự kiện xảy ra khi giao dịch bị hủy.

## Ví Dụ
### Ví dụ Cơ Bản
```javascript
let request = indexedDB.open("MyDatabase", 1);

request.onsuccess = function(event) {
    let db = event.target.result;
    let transaction = db.transaction(["MyObjectStore"], "readwrite");

    transaction.oncomplete = function() {
        console.log("Giao dịch hoàn tất.");
    };

    transaction.onerror = function() {
        console.log("Có lỗi xảy ra trong giao dịch.");
    };

    let objectStore = transaction.objectStore("MyObjectStore");
    let addRequest = objectStore.add({ id: 1, name: "John Doe" });

    addRequest.onsuccess = function() {
        console.log("Dữ liệu đã được thêm thành công.");
    };
};
```

## Giải Thích
### Những Lỗi Thường Gặp
- **Quên kiểm tra trạng thái giao dịch**: Kiểm tra trạng thái giao dịch trước khi thực hiện các thao tác là rất quan trọng để tránh lỗi.
- **Sử dụng sai chế độ giao dịch**: Nếu bạn muốn thực hiện các thay đổi, hãy chắc chắn rằng bạn đã khởi tạo giao dịch với chế độ "readwrite".
- **Xử lý sự kiện không chính xác**: Đảm bảo rằng bạn đã xử lý tất cả các sự kiện như `complete`, `error`, và `abort` để có thể quản lý giao dịch một cách hiệu quả.

## Tóm Tắt Một Dòng
IDBTransaction trong JavaScript là một công cụ mạnh mẽ cho phép thực hiện các thao tác giao dịch an toàn trên cơ sở dữ liệu IndexedDB.