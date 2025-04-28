<!--
Meta Description: # URIError trong JavaScript: Hiểu Biết và Cách Sử Dụng ## Tóm Tắt URIError là một loại lỗi trong JavaScript xảy ra khi có vấn đề với việc mã hóa hoặc ...
Meta Keywords: trong, uri, urierror, các, dụng
-->

# URIError trong JavaScript: Hiểu Biết và Cách Sử Dụng

## Tóm Tắt
URIError là một loại lỗi trong JavaScript xảy ra khi có vấn đề với việc mã hóa hoặc giải mã URI (Uniform Resource Identifier). Lỗi này thường xuất hiện khi sử dụng các phương thức như `decodeURI()` và `decodeURIComponent()`.

## Tài Liệu
URIError là một trong những loại lỗi được định nghĩa sẵn trong JavaScript, và nó biểu thị rằng có một vấn đề trong quá trình xử lý URI. Điều này thường xảy ra khi:

- Các ký tự không hợp lệ được sử dụng trong một URI.
- Các ký tự được mã hóa không đúng cách, dẫn đến không thể giải mã.

### Mục Đích
URIError giúp các lập trình viên phát hiện và xử lý các lỗi liên quan đến URI trong mã của họ, từ đó cải thiện khả năng xử lý lỗi và tính ổn định của ứng dụng.

### Cách Sử Dụng
Khi bạn cần giải mã một URI, sử dụng các phương thức `decodeURI()` hoặc `decodeURIComponent()`. Nếu có lỗi xảy ra trong quá trình này, một URIError sẽ được ném ra.

#### Ví dụ:
```javascript
try {
    const decodedURI = decodeURIComponent('%20invalid%URI');
} catch (e) {
    if (e instanceof URIError) {
        console.error('URIError: ' + e.message);
    }
}
```

## Ví Dụ
### Ví Dụ 1: Giải Mã URI Hợp Lệ
```javascript
const validURI = "https%3A%2F%2Fexample.com%2Fpath";
const decodedURI = decodeURIComponent(validURI);
console.log(decodedURI); // Kết quả: https://example.com/path
```

### Ví Dụ 2: Giải Mã URI Không Hợp Lệ
```javascript
try {
    const invalidURI = "https%3A%2F%2Fexample.com%2Fpath%";
    decodeURIComponent(invalidURI);
} catch (e) {
    console.error(e); // Kết quả: URIError: URI malformed
}
```

## Giải Thích
Khi làm việc với URIs, điều quan trọng là đảm bảo rằng các ký tự được mã hóa đúng cách. Một số lỗi phổ biến mà lập trình viên có thể gặp phải bao gồm:

- Sử dụng ký tự không hợp lệ trong URI.
- Mã hóa không đúng cách, như thiếu ký tự '%' trong mã hóa.
- Việc sử dụng các phương thức giải mã mà không kiểm tra trước các ký tự hợp lệ có thể dẫn đến lỗi.

Để tránh URIError, hãy luôn kiểm tra và xác nhận rằng URI của bạn được mã hóa đúng cách trước khi thực hiện giải mã.

## Tóm Tắt Một Dòng
URIError trong JavaScript là lỗi phát sinh khi có sự cố trong việc mã hóa hoặc giải mã URI, thường liên quan đến việc sử dụng các phương thức decodeURI() và decodeURIComponent().