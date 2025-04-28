<!--
Meta Description: # ReadableStream trong JavaScript: Hiểu Biết Cơ Bản và Cách Sử Dụng ## Tóm tắt `ReadableStream` là một phần quan trọng trong API Streams của JavaScrip...
Meta Keywords: liệu, stream, controller, readablestream, dụng
-->

# ReadableStream trong JavaScript: Hiểu Biết Cơ Bản và Cách Sử Dụng

## Tóm tắt
`ReadableStream` là một phần quan trọng trong API Streams của JavaScript, cho phép xử lý dữ liệu một cách hiệu quả bằng cách cung cấp khả năng đọc dữ liệu theo từng khối (chunk) mà không cần tải toàn bộ dữ liệu vào bộ nhớ.

## Tài liệu
### Mục đích
`ReadableStream` được thiết kế để làm việc với dữ liệu có thể được đọc theo từng khối, giúp giảm thiểu tải trọng bộ nhớ và cải thiện hiệu suất trong các ứng dụng web. Nó lý tưởng cho các tình huống như xử lý tệp tin lớn, tải dữ liệu từ mạng hoặc bất kỳ nguồn dữ liệu nào khác.

### Cách sử dụng
Để tạo một `ReadableStream`, bạn có thể sử dụng cú pháp sau:

```javascript
const stream = new ReadableStream({
    start(controller) {
        // Khởi tạo stream, có thể thêm dữ liệu vào controller
    },
    pull(controller) {
        // Gọi hàm này khi cần thêm dữ liệu vào stream
    },
    cancel() {
        // Xử lý khi stream bị hủy
    }
});
```

### Chi tiết
- **start(controller)**: Hàm này được gọi khi stream được khởi tạo. Bạn có thể sử dụng controller để thêm dữ liệu vào stream.
- **pull(controller)**: Hàm này được gọi khi consumer cần thêm dữ liệu. Bạn nên thêm dữ liệu vào controller trong hàm này.
- **cancel()**: Hàm này được gọi khi stream bị hủy. Bạn có thể thực hiện các hành động dọn dẹp ở đây.

## Ví dụ
Dưới đây là một ví dụ cơ bản về cách sử dụng `ReadableStream` để đọc dữ liệu từ một mảng:

```javascript
const data = [1, 2, 3, 4, 5];

const stream = new ReadableStream({
    start(controller) {
        data.forEach(item => controller.enqueue(item));
        controller.close();
    }
});

const reader = stream.getReader();

reader.read().then(({ done, value }) => {
    console.log(value); // In ra từng giá trị
});
```

## Giải thích
- **Những cạm bẫy phổ biến**: Một số nhà phát triển có thể gặp khó khăn trong việc quản lý các trạng thái của stream, chẳng hạn như không gọi `controller.close()` khi dữ liệu đã được gửi hết. Điều này có thể dẫn đến tình trạng không bao giờ hoàn thành stream.
- **Ghi nhớ**: `ReadableStream` không tự động xử lý các lỗi, vì vậy bạn nên có các biện pháp xử lý lỗi trong mã của mình để đảm bảo rằng ứng dụng của bạn không gặp sự cố.

## Tóm tắt một câu
`ReadableStream` trong JavaScript cung cấp một cách hiệu quả để đọc dữ liệu theo từng khối, giảm tải bộ nhớ và cải thiện hiệu suất ứng dụng.