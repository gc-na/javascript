<!--
Meta Description: # TextDecoderStream trong JavaScript: Giải mã văn bản một cách hiệu quả ## Tóm tắt `TextDecoderStream` là một giao diện trong JavaScript cho phép giải...
Meta Keywords: một, textdecoderstream, giải, luồng, bản
-->

# TextDecoderStream trong JavaScript: Giải mã văn bản một cách hiệu quả

## Tóm tắt
`TextDecoderStream` là một giao diện trong JavaScript cho phép giải mã các chuỗi byte thành định dạng văn bản trong các luồng (streams) một cách hiệu quả, giúp xử lý dữ liệu nhị phân dễ dàng hơn.

## Tài liệu
### Mục đích
`TextDecoderStream` được thiết kế để giải mã dữ liệu nhị phân thành chuỗi văn bản theo cách không đồng bộ, giúp cải thiện hiệu suất khi làm việc với các luồng dữ liệu lớn.

### Cách sử dụng
`TextDecoderStream` có thể được sử dụng để tạo một luồng giải mã mà có thể đọc từ một luồng nhị phân (như `ReadableStream`) và xuất ra một luồng văn bản (như `WritableStream`). 

#### Cú pháp
```javascript
const decoderStream = new TextDecoderStream(label, options);
```

- `label` (tùy chọn): Một chuỗi xác định bộ mã hóa (encoding) như "utf-8", "iso-8859-2", v.v.
- `options` (tùy chọn): Một đối tượng chứa các tùy chọn như `fatal` (boolean) chỉ định việc xử lý lỗi.

### Chi tiết
- Đối tượng `TextDecoderStream` có thể được sử dụng cùng với các luồng khác, giúp dễ dàng chuyển đổi giữa các loại dữ liệu.
- Nó là một phần của API Streams trong JavaScript, cho phép bạn thao tác với các luồng nhị phân và văn bản một cách linh hoạt.
- Khi dữ liệu được ghi vào `TextDecoderStream`, nó sẽ tự động giải mã và cung cấp chuỗi văn bản cho luồng đầu ra.

## Ví dụ
### Ví dụ cơ bản
```javascript
const { ReadableStream, WritableStream } = require('stream/web');

const decoderStream = new TextDecoderStream('utf-8');
const readableStream = new ReadableStream({
  start(controller) {
    const data = new Uint8Array([72, 101, 108, 108, 111]); // "Hello" in UTF-8
    controller.enqueue(data);
    controller.close();
  }
});

const writableStream = new WritableStream({
  write(chunk) {
    console.log(chunk); // In ra "Hello"
  }
});

readableStream
  .pipeTo(decoderStream)
  .then(() => decoderStream.readable.pipeTo(writableStream));
```

## Giải thích
- **Cảnh báo**: Đảm bảo rằng bạn sử dụng `TextDecoderStream` trong môi trường hỗ trợ API Streams. Một số trình duyệt cũ có thể không hỗ trợ tính năng này.
- **Lưu ý về bộ mã hóa**: Việc chọn bộ mã hóa không chính xác có thể dẫn đến lỗi khi giải mã. Hãy chắc chắn rằng byte data tương ứng với bộ mã hóa đã chọn.
- **Xử lý lỗi**: Nếu thuộc tính `fatal` được đặt thành `true`, lỗi giải mã sẽ ném ra ngoại lệ thay vì tiếp tục giải mã với dữ liệu bị lỗi.

## Tóm tắt một câu
`TextDecoderStream` trong JavaScript là một công cụ mạnh mẽ cho phép giải mã dữ liệu nhị phân thành chuỗi văn bản trong các luồng một cách linh hoạt và hiệu quả.