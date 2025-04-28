<!--
Meta Description: # Điều hướng trong JavaScript: Hướng dẫn chi tiết ## Tóm tắt Điều hướng trong JavaScript chủ yếu liên quan đến việc sử dụng đối tượng `window.location...
Meta Keywords: hướng, window, location, url, điều
-->

# Điều hướng trong JavaScript: Hướng dẫn chi tiết

## Tóm tắt
Điều hướng trong JavaScript chủ yếu liên quan đến việc sử dụng đối tượng `window.location` và các phương thức để quản lý URL, điều hướng trang, và tương tác với lịch sử trình duyệt.

## Tài liệu
### Mục đích
Điều hướng trong JavaScript cho phép lập trình viên điều khiển và thay đổi URL của trình duyệt, từ đó giúp người dùng chuyển hướng giữa các trang web hoặc thay đổi trạng thái của một ứng dụng web mà không cần tải lại trang.

### Sử dụng
Đối tượng `window.location` chứa thông tin về URL hiện tại của trang web và cung cấp các phương thức để thay đổi URL hoặc điều hướng đến trang khác. Một số phương thức phổ biến bao gồm:

- `window.location.href`: Để lấy hoặc gán URL của trang hiện tại.
- `window.location.replace(url)`: Thay thế URL hiện tại bằng URL mới mà không lưu lại lịch sử.
- `window.location.assign(url)`: Chuyển hướng đến một URL mới và lưu lại lịch sử.

### Chi tiết
- **window.location.href**: Khi bạn thiết lập giá trị cho `href`, trình duyệt sẽ chuyển hướng đến URL đó.
  
  ```javascript
  window.location.href = 'https://example.com';
  ```

- **window.location.replace()**: Phương thức này rất hữu ích khi bạn không muốn người dùng quay lại trang trước đó bằng nút "Quay lại" của trình duyệt.

  ```javascript
  window.location.replace('https://example.com');
  ```

- **window.location.assign()**: Phương thức này cho phép bạn điều hướng đến một trang mới nhưng lưu lại trang hiện tại trong lịch sử.

  ```javascript
  window.location.assign('https://example.com');
  ```

## Ví dụ
### Ví dụ 1: Chuyển hướng đến một trang khác
```javascript
function redirectToExample() {
    window.location.href = 'https://example.com';
}
```

### Ví dụ 2: Thay thế URL mà không lưu lịch sử
```javascript
function replaceCurrentPage() {
    window.location.replace('https://example.com');
}
```

### Ví dụ 3: Sử dụng assign để chuyển hướng
```javascript
function navigateToExample() {
    window.location.assign('https://example.com');
}
```

## Giải thích
- **Lưu ý về lịch sử**: Sử dụng `replace` nếu bạn không muốn người dùng có thể quay lại trang trước đó. Điều này thường hữu ích trong các ứng dụng web mà bạn không muốn người dùng trở lại trạng thái cũ.
- **Ràng buộc về cùng miền**: Một số trình duyệt có thể không cho phép điều hướng giữa các miền khác nhau do chính sách bảo mật cùng miền (same-origin policy).
- **Thời điểm gọi**: Đảm bảo rằng bạn chỉ thực hiện điều hướng sau khi DOM đã được tải xong, nếu không có thể gây ra lỗi hoặc hành vi không mong muốn.

## Tóm tắt một câu
Điều hướng trong JavaScript cho phép lập trình viên thay đổi URL và kiểm soát lịch sử trình duyệt để cải thiện trải nghiệm người dùng.