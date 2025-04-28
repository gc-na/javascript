<!--
Meta Description: # Hàm close trong JavaScript: Đóng cửa sổ hoặc tab ## Tóm tắt Hàm `close` trong JavaScript được sử dụng để đóng cửa sổ hoặc tab trình duyệt hiện tại. ...
Meta Keywords: cửa, đóng, close, javascript, hàm
-->

# Hàm close trong JavaScript: Đóng cửa sổ hoặc tab

## Tóm tắt
Hàm `close` trong JavaScript được sử dụng để đóng cửa sổ hoặc tab trình duyệt hiện tại. Hàm này chủ yếu được áp dụng cho các cửa sổ được mở thông qua JavaScript.

## Tài liệu
Hàm `close` là một phương thức của đối tượng `Window` trong JavaScript. Nó cho phép lập trình viên đóng một cửa sổ hoặc tab mà họ đã mở bằng phương thức `open`. Để sử dụng hàm này, cần đảm bảo rằng cửa sổ hoặc tab đó được mở bởi cùng một mã JavaScript, nếu không, trình duyệt sẽ không cho phép đóng.

### Cú pháp
```javascript
window.close();
```

### Mục đích
Mục đích chính của hàm `close` là để cải thiện trải nghiệm người dùng bằng cách cho phép đóng cửa sổ hoặc tab không còn cần thiết.

### Sử dụng
- Chỉ có thể sử dụng `window.close()` trên cửa sổ mà đã được mở thông qua JavaScript.
- Không thể đóng trang chính hoặc các tab được mở bằng cách nhập địa chỉ URL trực tiếp.

## Ví dụ
### Ví dụ 1: Đóng cửa sổ đã mở
```javascript
// Mở một cửa sổ mới
var newWindow = window.open('https://example.com', '_blank');

// Đóng cửa sổ mới
newWindow.close();
```

### Ví dụ 2: Cảnh báo trước khi đóng
```javascript
var newWindow = window.open('https://example.com', '_blank');

function closeWindow() {
    if (confirm('Bạn có chắc chắn muốn đóng cửa sổ này?')) {
        newWindow.close();
    }
}

// Gọi hàm đóng cửa sổ
closeWindow();
```

## Giải thích
- **Lưu ý về quyền hạn**: Trình duyệt sẽ không cho phép đóng một cửa sổ nếu nó không được mở bởi JavaScript. Nếu bạn cố gắng đóng một cửa sổ chính hoặc một cửa sổ được mở từ URL, hàm `close` sẽ không hoạt động.
- **Hạn chế bảo mật**: Một số trình duyệt có thể hạn chế việc sử dụng `window.close` để ngăn chặn các hành vi không mong muốn từ mã độc hại.
- **Trình duyệt khác nhau**: Hành vi của hàm `close` có thể khác nhau giữa các trình duyệt, vì vậy hãy kiểm tra kỹ lưỡng trên nhiều trình duyệt để đảm bảo tính tương thích.

## Tóm tắt một dòng
Hàm `close` trong JavaScript cho phép lập trình viên đóng cửa sổ hoặc tab đã mở bằng mã JavaScript, nhưng chỉ có thể áp dụng cho các cửa sổ được mở từ mã đó.