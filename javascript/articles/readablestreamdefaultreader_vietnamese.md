<!--
Meta Description: # Đọc Dữ Liệu với ReadableStreamDefaultReader trong JavaScript ## Tóm Tắt `ReadableStreamDefaultReader` là một giao diện trong JavaScript cho phép bạn...
Meta Keywords: một, liệu, bạn, đọc, readablestreamdefaultreader
-->

# Đọc Dữ Liệu với ReadableStreamDefaultReader trong JavaScript

## Tóm Tắt
`ReadableStreamDefaultReader` là một giao diện trong JavaScript cho phép bạn đọc dữ liệu từ một `ReadableStream`. Nó cung cấp các phương thức để lấy và xử lý dữ liệu một cách hiệu quả.

## Tài Liệu
`ReadableStreamDefaultReader` là một phần của API Streams trong JavaScript, cho phép bạn tương tác với các luồng dữ liệu mà không cần phải tải toàn bộ dữ liệu vào bộ nhớ. Giao diện này cung cấp các phương thức chính như `read()`, `releaseLock()`, và `closed`, giúp bạn quản lý việc đọc dữ liệu từ luồng một cách linh hoạt.

### Mục Đích
Mục đích chính của `ReadableStreamDefaultReader` là cho phép người dùng lấy dữ liệu từ một `ReadableStream` theo cách không đồng bộ. Điều này cực kỳ hữu ích khi làm việc với dữ liệu lớn hoặc khi bạn cần xử lý dữ liệu theo từng phần.

### Cách Sử Dụng
Để sử dụng `ReadableStreamDefaultReader`, bạn cần tạo một instance của `ReadableStream`, sau đó tạo một reader từ stream đó:

```javascript
const stream = new ReadableStream({
  start(controller) {
    controller.enqueue('Hello');
    controller.enqueue('World');
    controller.close();
  }
});

const reader = stream.getReader();
```

### Phương Thức Chính
- **read()**: Phương thức này đọc dữ liệu từ stream. Nó trả về một Promise chứa một đối tượng với hai thuộc tính: `value` (giá trị đọc được) và `done` (cho biết liệu stream đã kết thúc hay chưa).
- **releaseLock()**: Phương thức này giải phóng quyền sở hữu của reader đối với stream.
- **closed**: Một Promise cho biết khi nào reader đã hoàn thành việc đọc.

## Ví Dụ
### Ví Dụ Đơn Giản
Dưới đây là một ví dụ đơn giản về cách sử dụng `ReadableStreamDefaultReader` để đọc dữ liệu:

```javascript
const stream = new ReadableStream({
  start(controller) {
    controller.enqueue('Hello');
    controller.enqueue('World');
    controller.close();
  }
});

const reader = stream.getReader();

async function readStream() {
  let result;
  while (!(result = await reader.read()).done) {
    console.log(result.value); // In ra 'Hello' và 'World'
  }
}

readStream();
```

## Giải Thích
Khi sử dụng `ReadableStreamDefaultReader`, bạn cần chú ý một số điều sau:
- Đảm bảo rằng bạn không gọi `read()` trên một reader đã được giải phóng bằng `releaseLock()`, vì điều này sẽ dẫn đến lỗi.
- Nếu bạn không xử lý Promise trả về từ `read()`, luồng có thể không hoạt động đúng như mong đợi.
- Kiểm tra thuộc tính `done` trong kết quả trả về từ `read()` để biết khi nào luồng đã kết thúc.

## Tóm Tắt Một Dòng
`ReadableStreamDefaultReader` là giao diện cho phép bạn đọc dữ liệu từ `ReadableStream` trong JavaScript một cách hiệu quả và không đồng bộ.