<!--
Meta Description: # URL trong JavaScript: Tìm Hiểu và Sử Dụng ## Tóm tắt URL (Uniform Resource Locator) là một chuỗi ký tự được sử dụng để xác định vị trí của tài nguyê...
Meta Keywords: url, quả, javascript, đối, tượng
-->

# URL trong JavaScript: Tìm Hiểu và Sử Dụng

## Tóm tắt
URL (Uniform Resource Locator) là một chuỗi ký tự được sử dụng để xác định vị trí của tài nguyên trên Internet. Trong JavaScript, đối tượng `URL` cho phép bạn phân tích, xây dựng và quản lý các URL một cách hiệu quả.

## Tài liệu
### Mục đích
Đối tượng `URL` trong JavaScript được sử dụng để tạo và xử lý các URL. Nó giúp lập trình viên dễ dàng truy cập các thành phần khác nhau của URL như giao thức, tên miền, đường dẫn, và các tham số truy vấn.

### Cách sử dụng
Để sử dụng đối tượng `URL`, bạn chỉ cần khởi tạo một đối tượng mới bằng cách truyền vào chuỗi URL. Ví dụ:

```javascript
const myUrl = new URL('https://www.example.com/path?query=1');
```

### Chi tiết
- **Thành phần URL**: Đối tượng `URL` chia URL thành các phần như `protocol`, `hostname`, `pathname`, `search`, và `hash`.
- **Thêm và sửa đổi tham số truy vấn**: Bạn có thể dễ dàng thêm hoặc thay đổi tham số truy vấn bằng thuộc tính `searchParams` của đối tượng `URL`.

Ví dụ:
```javascript
myUrl.searchParams.append('newParam', 'value');
console.log(myUrl.href); // Kết quả: https://www.example.com/path?query=1&newParam=value
```

## Ví dụ
### Tạo URL
```javascript
const url = new URL('https://www.example.com:8080/path?name=test#section1');
console.log(url.protocol); // Kết quả: "https:"
console.log(url.hostname);  // Kết quả: "www.example.com"
console.log(url.port);      // Kết quả: "8080"
console.log(url.pathname);  // Kết quả: "/path"
console.log(url.search);    // Kết quả: "?name=test"
console.log(url.hash);      // Kết quả: "#section1"
```

### Thay đổi URL
```javascript
url.pathname = '/newPath';
url.searchParams.set('name', 'newTest');
console.log(url.href); // Kết quả: https://www.example.com:8080/newPath?name=newTest
```

## Giải thích
### Cạm bẫy phổ biến
- **Ghi nhớ quy tắc CORS**: Khi thực hiện yêu cầu từ trình duyệt, hãy chú ý đến quy tắc CORS (Cross-Origin Resource Sharing) để tránh lỗi khi truy cập tài nguyên từ miền khác.
- **Thao tác với `searchParams`**: Phương thức `append` và `set` có thể gây nhầm lẫn. `append` thêm nhiều tham số cùng tên, trong khi `set` chỉ giữ lại tham số cuối cùng.

### Lưu ý thêm
- Đối tượng `URL` có thể không hoạt động đúng trên các trình duyệt cũ hơn. Kiểm tra tính tương thích trước khi sử dụng.
- Sử dụng `URLSearchParams` để thao tác với các tham số truy vấn một cách linh hoạt và dễ dàng.

## Tóm tắt một dòng
Đối tượng `URL` trong JavaScript cho phép tạo, phân tích và quản lý các URL một cách hiệu quả và đơn giản.