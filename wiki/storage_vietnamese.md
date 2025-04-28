<!--
Meta Description: # Lưu Trữ trong JavaScript: Hướng Dẫn Chi Tiết ## Tóm Tắt Lưu trữ trong JavaScript đề cập đến các phương pháp lưu trữ dữ liệu trên trình duyệt, cho ph...
Meta Keywords: lưu, liệu, trữ, storage, trong
-->

# Lưu Trữ trong JavaScript: Hướng Dẫn Chi Tiết

## Tóm Tắt
Lưu trữ trong JavaScript đề cập đến các phương pháp lưu trữ dữ liệu trên trình duyệt, cho phép các ứng dụng web lưu trữ thông tin một cách bền vững và dễ dàng truy cập.

## Tài Liệu
Lưu trữ dữ liệu là một phần quan trọng trong phát triển ứng dụng web. JavaScript cung cấp nhiều API để lưu trữ thông tin, bao gồm:

1. **Local Storage**: Cho phép lưu trữ dữ liệu dưới dạng key-value trong trình duyệt, tồn tại ngay cả khi người dùng đóng trình duyệt.
2. **Session Storage**: Tương tự như Local Storage nhưng chỉ tồn tại trong phiên làm việc hiện tại của trình duyệt.
3. **IndexedDB**: Cơ sở dữ liệu NoSQL cho phép lưu trữ và truy vấn dữ liệu phức tạp hơn.

### Sử Dụng
- **Local Storage**:
  ```javascript
  // Lưu trữ dữ liệu
  localStorage.setItem('key', 'value');

  // Lấy dữ liệu
  const value = localStorage.getItem('key');

  // Xóa dữ liệu
  localStorage.removeItem('key');
  ```

- **Session Storage**:
  ```javascript
  // Lưu trữ dữ liệu
  sessionStorage.setItem('sessionKey', 'sessionValue');

  // Lấy dữ liệu
  const sessionValue = sessionStorage.getItem('sessionKey');

  // Xóa dữ liệu
  sessionStorage.removeItem('sessionKey');
  ```

- **IndexedDB**:
  ```javascript
  let request = indexedDB.open('myDatabase', 1);

  request.onupgradeneeded = function(event) {
    let db = event.target.result;
    db.createObjectStore('myStore', { keyPath: 'id' });
  };

  request.onsuccess = function(event) {
    let db = event.target.result;
    let transaction = db.transaction(['myStore'], 'readwrite');
    let store = transaction.objectStore('myStore');
    store.add({ id: 1, name: 'Item 1' });
  };
  ```

## Giải Thích
- **Local Storage**: Dữ liệu được lưu trữ không có thời gian hết hạn và có thể được truy cập từ bất kỳ trang nào trong cùng một domain.
- **Session Storage**: Dữ liệu chỉ tồn tại trong phiên làm việc hiện tại, và khi người dùng đóng tab hoặc trình duyệt, dữ liệu sẽ bị xóa.
- **IndexedDB**: Cung cấp khả năng lưu trữ dữ liệu phức tạp hơn, cho phép lưu trữ các đối tượng và thực hiện truy vấn trên chúng. Tuy nhiên, việc làm việc với IndexedDB có thể phức tạp hơn so với Local và Session Storage.

### Những Lưu Ý Thông Thường
- Dữ liệu lưu trữ trong Local và Session Storage đều có kích thước giới hạn (thông thường khoảng 5MB).
- Tránh lưu trữ thông tin nhạy cảm như mật khẩu trong Local hoặc Session Storage vì chúng có thể dễ dàng bị truy cập bởi bất kỳ mã JavaScript nào chạy trên cùng một trang.
- IndexedDB yêu cầu xử lý bất đồng bộ, vì vậy bạn nên quen thuộc với Promise hoặc async/await khi làm việc với nó.

## Tóm Tắt Một Dòng
Lưu trữ trong JavaScript cho phép lưu trữ dữ liệu trên trình duyệt thông qua Local Storage, Session Storage và IndexedDB, phục vụ cho nhiều mục đích khác nhau trong phát triển ứng dụng web.