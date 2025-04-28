<!--
Meta Description: # IDBDatabase trong JavaScript: Cơ sở dữ liệu trên trình duyệt ## Tóm tắt IDBDatabase là một phần của API IndexedDB trong JavaScript, cho phép lưu trữ...
Meta Keywords: liệu, một, const, event, lưu
-->

# IDBDatabase trong JavaScript: Cơ sở dữ liệu trên trình duyệt

## Tóm tắt
IDBDatabase là một phần của API IndexedDB trong JavaScript, cho phép lưu trữ dữ liệu có cấu trúc lớn trên trình duyệt. Nó cung cấp một cách hiệu quả để lưu trữ và truy xuất dữ liệu không đồng bộ.

## Tài liệu
### Mục đích
IDBDatabase đại diện cho một cơ sở dữ liệu trong IndexedDB. Nó cho phép người dùng thực hiện các thao tác như tạo đối tượng lưu trữ, thêm, sửa đổi, và xóa dữ liệu. API này được thiết kế để xử lý lượng dữ liệu lớn và hỗ trợ các ứng dụng web yêu cầu lưu trữ offline hoặc đồng bộ hóa dữ liệu.

### Cách sử dụng
Để sử dụng IDBDatabase, bạn cần tạo một kết nối đến IndexedDB thông qua `indexedDB.open()`. Sau khi cơ sở dữ liệu được mở thành công, bạn có thể thực hiện các thao tác trên nó.

#### Cú pháp cơ bản
```javascript
const request = indexedDB.open('MyDatabase', 1);

request.onsuccess = function(event) {
    const db = event.target.result;
    // Thực hiện các thao tác với cơ sở dữ liệu ở đây
};

request.onerror = function(event) {
    console.error('Lỗi khi mở cơ sở dữ liệu:', event.target.error);
};
```

### Chi tiết
IDBDatabase cung cấp một loạt các phương thức và thuộc tính để làm việc với cơ sở dữ liệu. Một số phương thức chính bao gồm:

- **createObjectStore(name, options)**: Tạo một đối tượng lưu trữ mới trong cơ sở dữ liệu.
- **transaction(storeNames, mode)**: Bắt đầu một giao dịch với các đối tượng lưu trữ chỉ định.
- **close()**: Đóng kết nối đến cơ sở dữ liệu.

### Ví dụ
Dưới đây là một ví dụ đơn giản về cách tạo một cơ sở dữ liệu và thêm một đối tượng lưu trữ:

```javascript
const request = indexedDB.open('MyDatabase', 1);

request.onupgradeneeded = function(event) {
    const db = event.target.result;
    const objectStore = db.createObjectStore('users', { keyPath: 'id' });
    objectStore.createIndex('name', 'name', { unique: false });
};

request.onsuccess = function(event) {
    const db = event.target.result;
    const transaction = db.transaction('users', 'readwrite');
    const objectStore = transaction.objectStore('users');

    const user = { id: 1, name: 'Nguyễn Văn A' };
    const requestAdd = objectStore.add(user);

    requestAdd.onsuccess = function() {
        console.log('Người dùng đã được thêm thành công!');
    };
};

request.onerror = function(event) {
    console.error('Lỗi khi mở cơ sở dữ liệu:', event.target.error);
};
```

### Giải thích
Khi làm việc với IDBDatabase, có một số vấn đề phổ biến mà bạn nên lưu ý:

- **Trình duyệt hỗ trợ**: Không phải tất cả các trình duyệt đều hỗ trợ IndexedDB. Hãy kiểm tra tính tương thích trước khi sử dụng.
- **Khả năng đồng bộ**: IDBDatabase hoạt động không đồng bộ, vì vậy bạn cần xử lý các sự kiện thành công và lỗi để đảm bảo không có vấn đề xảy ra trong quá trình thực hiện.
- **Quản lý phiên bản**: Khi thay đổi cấu trúc cơ sở dữ liệu, bạn phải sử dụng sự kiện `onupgradeneeded` để thực hiện các thay đổi cần thiết.

## Tóm tắt một dòng
IDBDatabase là một phần của API IndexedDB trong JavaScript, cho phép lưu trữ và truy xuất dữ liệu không đồng bộ trong trình duyệt một cách hiệu quả.