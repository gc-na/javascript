<!--
Meta Description: # localStorage trong JavaScript: Lưu trữ dữ liệu trên trình duyệt ## Tóm tắt `localStorage` là một API trong JavaScript cho phép lưu trữ dữ liệu dưới ...
Meta Keywords: localstorage, liệu, lưu, trữ, một
-->

# localStorage trong JavaScript: Lưu trữ dữ liệu trên trình duyệt

## Tóm tắt
`localStorage` là một API trong JavaScript cho phép lưu trữ dữ liệu dưới dạng cặp khóa-giá trị trên trình duyệt của người dùng. Dữ liệu được lưu trữ sẽ tồn tại ngay cả khi người dùng đóng trình duyệt.

## Tài liệu
`localStorage` là một phần của Web Storage API, cung cấp khả năng lưu trữ dữ liệu cục bộ cho ứng dụng web. Dữ liệu được lưu trữ trong `localStorage` sẽ không bị xóa khi người dùng đóng tab hoặc trình duyệt, giúp bạn có thể lưu trữ thông tin lâu dài cho người dùng. Dưới đây là một số thông tin cơ bản về `localStorage`:

### Mục đích
- Lưu trữ dữ liệu cục bộ cho ứng dụng web.
- Giúp cải thiện trải nghiệm người dùng bằng cách lưu giữ thông tin giữa các phiên làm việc.

### Cách sử dụng
- `localStorage.setItem(key, value)`: Lưu một giá trị vào `localStorage`.
- `localStorage.getItem(key)`: Lấy giá trị từ `localStorage`.
- `localStorage.removeItem(key)`: Xóa một mục khỏi `localStorage`.
- `localStorage.clear()`: Xóa tất cả dữ liệu trong `localStorage`.
- `localStorage.length`: Trả về số lượng mục hiện có trong `localStorage`.

### Chi tiết
Dữ liệu trong `localStorage` được lưu trữ dưới dạng chuỗi. Nếu bạn muốn lưu trữ một đối tượng, hãy sử dụng `JSON.stringify()` để chuyển đổi đối tượng thành chuỗi trước khi lưu, và `JSON.parse()` để chuyển đổi lại từ chuỗi thành đối tượng khi lấy dữ liệu.

## Ví dụ
```javascript
// Lưu trữ dữ liệu
localStorage.setItem('username', 'JohnDoe');

// Lấy dữ liệu
let username = localStorage.getItem('username');
console.log(username); // Kết quả: JohnDoe

// Xóa dữ liệu
localStorage.removeItem('username');

// Xóa tất cả dữ liệu
localStorage.clear();
```

## Giải thích
Mặc dù `localStorage` rất hữu ích, có một số điều cần lưu ý:
- Dữ liệu trong `localStorage` chỉ có thể được truy cập bởi cùng một nguồn (origin).
- Dung lượng lưu trữ thường giới hạn khoảng 5MB, tùy thuộc vào trình duyệt.
- `localStorage` chỉ lưu trữ dữ liệu dưới dạng chuỗi, vì vậy bạn cần chuyển đổi các kiểu dữ liệu khác.

## Tóm tắt một dòng
`localStorage` là một API trong JavaScript cho phép lưu trữ dữ liệu cục bộ trên trình duyệt, duy trì dữ liệu ngay cả khi người dùng đóng trang web.