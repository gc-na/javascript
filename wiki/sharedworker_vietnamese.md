<!--
Meta Description: # SharedWorker trong JavaScript: Hiểu Biết Cơ Bản và Ứng Dụng ## Tóm tắt SharedWorker là một loại Worker trong JavaScript cho phép nhiều tab hoặc cửa ...
Meta Keywords: sharedworker, worker, port, một, event
-->

# SharedWorker trong JavaScript: Hiểu Biết Cơ Bản và Ứng Dụng

## Tóm tắt
SharedWorker là một loại Worker trong JavaScript cho phép nhiều tab hoặc cửa sổ trong cùng một trình duyệt chia sẻ một instance duy nhất của worker, giúp tiết kiệm tài nguyên và đồng bộ hóa dữ liệu giữa các phiên làm việc.

## Tài liệu

### Mục đích
SharedWorker được thiết kế để cung cấp khả năng xử lý đa luồng cho các ứng dụng web, cho phép nhiều thành phần của ứng dụng (chẳng hạn như các tab hoặc iframe) tương tác với nhau qua một worker chung. Điều này cực kỳ hữu ích cho các ứng dụng cần chia sẻ trạng thái hoặc dữ liệu giữa các phần khác nhau của giao diện người dùng.

### Cách sử dụng
Để sử dụng SharedWorker, bạn cần thực hiện các bước sau:

1. **Tạo một file JavaScript cho worker**: Đầu tiên, bạn cần tạo một file riêng cho SharedWorker, nơi bạn viết mã cho worker.

```javascript
// sharedWorker.js
self.addEventListener('connect', function(event) {
    const port = event.ports[0];
    port.addEventListener('message', function(event) {
        port.postMessage('Received: ' + event.data);
    });
    port.start();
});
```

2. **Khởi tạo SharedWorker trong ứng dụng chính**: Trong file JavaScript chính của bạn, bạn khởi tạo SharedWorker và thiết lập kết nối.

```javascript
// main.js
const worker = new SharedWorker('sharedWorker.js');

worker.port.start();

worker.port.postMessage('Hello from main!');
worker.port.onmessage = function(event) {
    console.log(event.data); // "Received: Hello from main!"
};
```

### Chi tiết
- **Tính năng**: SharedWorker cho phép nhiều tab, cửa sổ hoặc iframe trong cùng một nguồn gốc (origin) chia sẻ một instance của worker, giúp tiết kiệm tài nguyên và cải thiện hiệu suất.
- **Kết nối**: Mỗi tab hoặc cửa sổ khi kết nối đến SharedWorker sẽ nhận được một `MessagePort` để giao tiếp với worker.
- **Quản lý trạng thái**: Bạn có thể sử dụng SharedWorker để quản lý trạng thái ứng dụng, như phiên người dùng, và dễ dàng chia sẻ thông tin này giữa các tab.

## Ví dụ

### Ví dụ Cơ Bản
```javascript
// sharedWorker.js
self.addEventListener('connect', function(event) {
    const port = event.ports[0];
    port.onmessage = function(event) {
        port.postMessage('Hello from SharedWorker!');
    };
    port.start();
});

// main.js
const worker = new SharedWorker('sharedWorker.js');
worker.port.start();

worker.port.postMessage('Ping');
worker.port.onmessage = function(event) {
    console.log(event.data); // "Hello from SharedWorker!"
};
```

## Giải thích
- **Khó khăn phổ biến**: Một số trình duyệt có thể không hỗ trợ SharedWorker hoàn toàn. Bạn nên kiểm tra tính tương thích trên các trình duyệt khác nhau trước khi triển khai.
- **Giới hạn**: SharedWorker chỉ có thể được sử dụng trong cùng một nguồn gốc (origin) và không thể chia sẻ giữa các nguồn gốc khác nhau.
- **Tin nhắn**: Khi gửi và nhận tin nhắn, cần đảm bảo rằng hai đầu (worker và main thread) đều đã khởi tạo và đang lắng nghe sự kiện tin nhắn.

## Tóm tắt một dòng
SharedWorker trong JavaScript cho phép nhiều tab hoặc cửa sổ chia sẻ một instance duy nhất của worker, giúp đồng bộ hóa dữ liệu và tiết kiệm tài nguyên.