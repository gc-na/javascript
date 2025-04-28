<!--
Meta Description: # decodeURIComponent: Giải mã chuỗi URL trong JavaScript ## Tóm tắt `decodeURIComponent` là một phương thức trong JavaScript được sử dụng để giải mã c...
Meta Keywords: chuỗi, các, decodeuricomponent, hóa, được
-->

# decodeURIComponent: Giải mã chuỗi URL trong JavaScript

## Tóm tắt
`decodeURIComponent` là một phương thức trong JavaScript được sử dụng để giải mã các chuỗi URL đã được mã hóa, giúp chuyển đổi các ký tự mã hóa trở về dạng ban đầu của chúng.

## Tài liệu
### Mục đích
`decodeURIComponent` chủ yếu được sử dụng để giải mã các phần của URL mà có thể chứa các ký tự đặc biệt, chẳng hạn như dấu cách, dấu chấm hỏi, và các ký tự không phải ASCII khác. Điều này rất hữu ích khi bạn cần xử lý các tham số trong URL hoặc khi bạn nhận dữ liệu từ một API.

### Cách sử dụng
Cú pháp của `decodeURIComponent` như sau:

```javascript
decodeURIComponent(encodedURI);
```

- **encodedURI**: Đây là chuỗi URL đã được mã hóa mà bạn muốn giải mã. Ví dụ: `%20` sẽ được chuyển thành dấu cách (` `).

### Chi tiết
- `decodeURIComponent` không thay đổi các ký tự không mã hóa trong chuỗi.
- Phương thức này ném ra một `URIError` nếu chuỗi được truyền vào không phải là một chuỗi mã hóa hợp lệ.

## Ví dụ
### Ví dụ cơ bản
```javascript
const encodedString = "Hello%20World%21";
const decodedString = decodeURIComponent(encodedString);
console.log(decodedString); // Kết quả: Hello World!
```

### Ví dụ với ký tự đặc biệt
```javascript
const encodedString = "T%C3%A0i%20li%E1%BB%87u%20JavaScript";
const decodedString = decodeURIComponent(encodedString);
console.log(decodedString); // Kết quả: Tài liệu JavaScript
```

## Giải thích
Một số lưu ý quan trọng khi sử dụng `decodeURIComponent`:
- Nếu bạn cố gắng giải mã một chuỗi không được mã hóa đúng cách, bạn sẽ gặp lỗi `URIError`. Chẳng hạn, chuỗi như "Hello%20World%2" sẽ gây ra lỗi.
- Để mã hóa chuỗi trước khi truyền qua URL, bạn có thể sử dụng phương thức `encodeURIComponent`.

### Các vấn đề phổ biến
- Đảm bảo rằng bạn chỉ giải mã các chuỗi đã được mã hóa bằng `encodeURIComponent` hoặc một phương pháp mã hóa tương tự. Nếu chuỗi không được mã hóa đúng cách, bạn có thể gặp lỗi.
- Không nên sử dụng `decodeURIComponent` cho các chuỗi mà không có sự kiểm soát, vì điều này có thể dẫn đến các vấn đề bảo mật, chẳng hạn như tấn công XSS (Cross-Site Scripting).

## Tóm tắt một dòng
`decodeURIComponent` là phương thức JavaScript dùng để giải mã các chuỗi URL đã mã hóa, giúp chuyển đổi các ký tự trở về dạng ban đầu của chúng.