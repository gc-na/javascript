<!--
Meta Description: # sessionStorage trong JavaScript: Lưu trữ dữ liệu phiên làm việc ## Tóm tắt `sessionStorage` là một phần của Web Storage API trong JavaScript, cho ph...
Meta Keywords: liệu, sessionstorage, lưu, trữ, trong
-->

# sessionStorage trong JavaScript: Lưu trữ dữ liệu phiên làm việc

## Tóm tắt
`sessionStorage` là một phần của Web Storage API trong JavaScript, cho phép lưu trữ dữ liệu cho phiên làm việc của trình duyệt. Dữ liệu được lưu trữ trong `sessionStorage` chỉ tồn tại trong suốt phiên làm việc hiện tại và sẽ bị xóa khi tab hoặc cửa sổ trình duyệt được đóng.

## Tài liệu
### Mục đích
`sessionStorage` được sử dụng để lưu trữ dữ liệu tạm thời cho một phiên làm việc duy nhất. Điều này có nghĩa là dữ liệu sẽ không được chia sẻ giữa các tab hoặc cửa sổ khác của cùng một trình duyệt.

### Cách sử dụng
Để sử dụng `sessionStorage`, bạn có thể truy cập nó thông qua đối tượng `window.sessionStorage`. Đây là các phương thức chính mà bạn có thể sử dụng:

- `setItem(key, value)`: Lưu trữ một cặp khóa-giá trị.
- `getItem(key)`: Lấy giá trị từ `sessionStorage` theo khóa.
- `removeItem(key)`: Xóa một cặp khóa-giá trị.
- `clear()`: Xóa tất cả dữ liệu trong `sessionStorage`.
- `key(index)`: Lấy tên khóa theo chỉ số.

### Chi tiết
Dữ liệu trong `sessionStorage` được lưu trữ dưới dạng chuỗi. Nếu bạn muốn lưu trữ các đối tượng hoặc mảng, bạn cần phải chuyển đổi chúng thành chuỗi với `JSON.stringify()` và sau đó chuyển đổi lại thành đối tượng với `JSON.parse()` khi lấy dữ liệu.

## Ví dụ
### Lưu trữ dữ liệu
```javascript
// Lưu trữ dữ liệu
sessionStorage.setItem('username', 'JohnDoe');
```

### Lấy dữ liệu
```javascript
// Lấy dữ liệu
const user = sessionStorage.getItem('username');
console.log(user); // Output: JohnDoe
```

### Xóa dữ liệu
```javascript
// Xóa dữ liệu
sessionStorage.removeItem('username');
```

### Xóa tất cả dữ liệu
```javascript
// Xóa tất cả dữ liệu
sessionStorage.clear();
```

### Lưu trữ đối tượng
```javascript
// Lưu trữ đối tượng
const user = { name: 'John', age: 30 };
sessionStorage.setItem('user', JSON.stringify(user));

// Lấy đối tượng
const retrievedUser = JSON.parse(sessionStorage.getItem('user'));
console.log(retrievedUser); // Output: { name: 'John', age: 30 }
```

## Giải thích
Mặc dù `sessionStorage` rất hữu ích, nhưng có một số điều cần lưu ý:
- Dữ liệu trong `sessionStorage` không được chia sẻ giữa các tab hoặc cửa sổ.
- Dữ liệu sẽ bị xóa khi cửa sổ hoặc tab trình duyệt bị đóng.
- Dung lượng lưu trữ của `sessionStorage` thường bị giới hạn (khoảng 5-10MB tùy theo trình duyệt).
- Nếu bạn cần lưu trữ dữ liệu lâu dài hơn, hãy sử dụng `localStorage` thay vì `sessionStorage`.

## Tóm tắt một dòng
`sessionStorage` cho phép lưu trữ dữ liệu tạm thời trong trình duyệt cho phiên làm việc hiện tại, giúp quản lý dữ liệu một cách hiệu quả trong các ứng dụng web.