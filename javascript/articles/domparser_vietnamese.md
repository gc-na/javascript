<!--
Meta Description: # DOMParser trong JavaScript: Hướng dẫn chi tiết và ví dụ ## Tóm tắt DOMParser là một giao diện trong JavaScript cho phép phân tích cú pháp chuỗi XML ...
Meta Keywords: liệu, tài, phân, tích, xml
-->

# DOMParser trong JavaScript: Hướng dẫn chi tiết và ví dụ

## Tóm tắt
DOMParser là một giao diện trong JavaScript cho phép phân tích cú pháp chuỗi XML hoặc HTML thành các đối tượng DOM, tạo điều kiện cho việc xử lý và tương tác với các tài liệu cấu trúc.

## Tài liệu
### Mục đích
DOMParser được sử dụng để chuyển đổi chuỗi văn bản dạng XML hoặc HTML thành một tài liệu DOM mà bạn có thể thao tác như các đối tượng JavaScript khác. Điều này rất hữu ích khi bạn cần làm việc với dữ liệu XML/HTML từ các nguồn bên ngoài hoặc từ chuỗi nội dung có sẵn.

### Cách sử dụng
Để sử dụng DOMParser, bạn cần tạo một thể hiện của nó và sau đó gọi phương thức `parseFromString()` với hai tham số: chuỗi cần phân tích và loại tài liệu (ví dụ: "text/html" hoặc "application/xml").

#### Cú pháp
```javascript
const parser = new DOMParser();
const doc = parser.parseFromString(string, contentType);
```

- `string`: Chuỗi XML hoặc HTML mà bạn muốn phân tích.
- `contentType`: Loại nội dung của chuỗi, thường là "text/html" cho HTML hoặc "application/xml" cho XML.

### Chi tiết
DOMParser là một phần của API DOM, cho phép bạn dễ dàng tạo các tài liệu DOM từ các chuỗi văn bản. Sau khi tài liệu được phân tích, bạn có thể sử dụng các phương thức và thuộc tính của DOM để truy cập và thao tác với các phần tử trong tài liệu.

## Ví dụ
### Ví dụ 1: Phân tích HTML
```javascript
const htmlString = '<div><p>Hello, World!</p></div>';
const parser = new DOMParser();
const doc = parser.parseFromString(htmlString, 'text/html');

console.log(doc.body.innerHTML);  // Kết quả: <div><p>Hello, World!</p></div>
```

### Ví dụ 2: Phân tích XML
```javascript
const xmlString = '<note><to>Tove</to><from>Jani</from><heading>Reminder</heading><body>Don\'t forget me this weekend!</body></note>';
const parser = new DOMParser();
const doc = parser.parseFromString(xmlString, 'application/xml');

console.log(doc.getElementsByTagName('to')[0].textContent);  // Kết quả: Tove
```

## Giải thích
- **Lỗi phân tích**: Nếu chuỗi không phải là một tài liệu hợp lệ, `parseFromString()` sẽ trả về một đối tượng DOM với các thông báo lỗi trong `parsererror`.
- **Kiểm tra lỗi**: Để kiểm tra xem tài liệu có được phân tích thành công hay không, bạn có thể kiểm tra `doc.getElementsByTagName('parsererror')`. Nếu có, tài liệu đã gặp lỗi.

```javascript
if (doc.getElementsByTagName('parsererror').length > 0) {
    console.error('Có lỗi trong khi phân tích tài liệu.');
}
```

## Tóm tắt một câu
DOMParser trong JavaScript cho phép bạn phân tích cú pháp chuỗi XML hoặc HTML thành các đối tượng DOM, giúp dễ dàng thao tác với dữ liệu cấu trúc.