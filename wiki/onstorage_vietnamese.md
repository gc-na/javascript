<!--
Meta Description: # Kiến thức về "onstorage" trong JavaScript: Sự kiện lưu trữ trong Trình duyệt ## Tóm tắt Sự kiện `onstorage` trong JavaScript là một sự kiện được kíc...
Meta Keywords: event, trong, kiện, thay, đổi
-->

# Kiến thức về "onstorage" trong JavaScript: Sự kiện lưu trữ trong Trình duyệt

## Tóm tắt
Sự kiện `onstorage` trong JavaScript là một sự kiện được kích hoạt khi có thay đổi trong Storage (Lưu trữ) của cửa sổ trình duyệt khác, giúp các ứng dụng web có thể đồng bộ hóa dữ liệu giữa các tab hoặc cửa sổ khác nhau.

## Tài liệu
### Mục đích
Sự kiện `onstorage` cho phép các nhà phát triển theo dõi và phản ứng khi có sự thay đổi về dữ liệu trong `localStorage` hoặc `sessionStorage`. Điều này rất hữu ích trong các ứng dụng web đa tab, nơi mà dữ liệu cần được đồng bộ hóa giữa các phiên làm việc khác nhau.

### Cách sử dụng
Để sử dụng sự kiện `onstorage`, bạn cần phải lắng nghe sự kiện này trên đối tượng `window`. Khi một tab hoặc cửa sổ khác thay đổi dữ liệu trong `localStorage` hoặc `sessionStorage`, sự kiện `onstorage` sẽ được kích hoạt và bạn có thể xử lý nó theo cách bạn muốn.

```javascript
window.addEventListener('storage', function(event) {
    console.log('Dữ liệu đã thay đổi!');
    console.log('Key:', event.key);
    console.log('Giá trị mới:', event.newValue);
    console.log('Giá trị cũ:', event.oldValue);
});
```

### Chi tiết
- **event.key**: Tên của khóa mà dữ liệu đã được thay đổi.
- **event.newValue**: Giá trị mới của khóa.
- **event.oldValue**: Giá trị cũ của khóa trước khi thay đổi.
- **event.storageArea**: Đối tượng lưu trữ (`localStorage` hoặc `sessionStorage`) mà sự kiện này được phát sinh từ đó.

## Ví dụ
### Ví dụ đơn giản
```javascript
// Lắng nghe sự kiện onstorage
window.addEventListener('storage', function(event) {
    alert(`Đã có thay đổi: ${event.key} đã được cập nhật từ ${event.oldValue} thành ${event.newValue}`);
});

// Cập nhật giá trị trong localStorage từ một tab khác
localStorage.setItem('user', 'Nguyễn Văn A');
```

### Ví dụ phức tạp hơn
```javascript
// Tab 1: Lắng nghe sự kiện onstorage
window.addEventListener('storage', function(event) {
    if (event.key === 'user') {
        console.log(`Người dùng đã thay đổi thành: ${event.newValue}`);
    }
});

// Tab 2: Cập nhật giá trị
function updateUser(newName) {
    localStorage.setItem('user', newName);
}
```

## Giải thích
### Những cạm bẫy thông thường
- **Không hoạt động trong cùng một tab**: Sự kiện `onstorage` chỉ được kích hoạt khi dữ liệu được thay đổi từ một tab hoặc cửa sổ khác. Nếu bạn thay đổi `localStorage` trong cùng một tab, sự kiện sẽ không được kích hoạt.
- **Thao tác bất đồng bộ**: Đôi khi, việc cập nhật dữ liệu trong `localStorage` có thể không diễn ra ngay lập tức, dẫn đến việc bạn có thể không nhận được giá trị mới ngay lập tức trong sự kiện `onstorage`.

## Tóm tắt một câu
Sự kiện `onstorage` trong JavaScript cho phép theo dõi và phản ứng với những thay đổi trong dữ liệu lưu trữ giữa các tab hoặc cửa sổ trình duyệt khác nhau.