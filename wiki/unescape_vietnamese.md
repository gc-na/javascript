<!--
Meta Description: # Hàm `unescape` trong JavaScript: Cách sử dụng và lưu ý ## Tóm tắt Hàm `unescape` trong JavaScript được sử dụng để giải mã các chuỗi đã được mã hóa b...
Meta Keywords: dụng, unescape, trong, các, chuỗi
-->

# Hàm `unescape` trong JavaScript: Cách sử dụng và lưu ý

## Tóm tắt
Hàm `unescape` trong JavaScript được sử dụng để giải mã các chuỗi đã được mã hóa bằng cách sử dụng hàm `escape`. Mặc dù `unescape` đã bị khuyến cáo không nên sử dụng trong các phiên bản JavaScript hiện đại, nó vẫn xuất hiện trong một số mã nguồn cũ.

## Tài liệu
### Mục đích
Hàm `unescape` được thiết kế để chuyển đổi các ký tự đặc biệt trong chuỗi đã được mã hóa lại về dạng ban đầu của chúng. Các ký tự ASCII không phải là ký tự chữ cái, số hoặc dấu câu sẽ được thay thế bằng mã hex của chúng.

### Cú pháp
```javascript
unescape(str);
```

**Tham số:**
- `str`: Chuỗi cần được giải mã.

### Trả về
Hàm trả về chuỗi đã được giải mã.

### Lưu ý
Hàm `unescape` đã bị loại bỏ trong ECMAScript 5 và không nên được sử dụng trong các ứng dụng hiện đại. Thay vào đó, bạn nên sử dụng `decodeURIComponent` hoặc `decodeURI` cho mục đích tương tự.

## Ví dụ
### Ví dụ 1: Giải mã chuỗi đơn giản
```javascript
let encodedStr = "Hello%20World%21"; // Chuỗi đã mã hóa
let decodedStr = unescape(encodedStr); // Giải mã chuỗi
console.log(decodedStr); // Kết quả: Hello World!
```

### Ví dụ 2: Giải mã chuỗi với ký tự đặc biệt
```javascript
let encodedStr = "JavaScript%20%26%20Java"; // Chuỗi đã mã hóa
let decodedStr = unescape(encodedStr);
console.log(decodedStr); // Kết quả: JavaScript & Java
```

## Giải thích
Mặc dù `unescape` có thể hoạt động tốt trong một số trường hợp đơn giản, nhưng có nhiều vấn đề có thể phát sinh:
- **Khuyến cáo không sử dụng**: Vì đã bị loại bỏ và không còn được hỗ trợ, việc sử dụng `unescape` có thể dẫn đến các lỗi trong mã nguồn và không đảm bảo tính tương thích với các trình duyệt hiện đại.
- **Sử dụng phương pháp thay thế**: Nên dùng `decodeURIComponent` hoặc `decodeURI` để giải mã chuỗi URL, vì chúng hỗ trợ đầy đủ các ký tự và không gặp phải những vấn đề với các ký tự không chuẩn.

## Tóm tắt một dòng
Hàm `unescape` trong JavaScript là một phương pháp cũ để giải mã các chuỗi mã hóa, nhưng không nên được sử dụng trong các ứng dụng hiện đại.