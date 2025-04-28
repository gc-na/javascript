<!--
Meta Description: # Sự kiện StorageEvent trong JavaScript: Tìm Hiểu và Ứng Dụng ## Tóm Tắt Sự kiện `StorageEvent` trong JavaScript xảy ra khi có sự thay đổi trong đối t...
Meta Keywords: kiện, đổi, thay, event, trong
-->

# Sự kiện StorageEvent trong JavaScript: Tìm Hiểu và Ứng Dụng

## Tóm Tắt
Sự kiện `StorageEvent` trong JavaScript xảy ra khi có sự thay đổi trong đối tượng `Storage`, bao gồm `localStorage` hoặc `sessionStorage`. Đây là một công cụ hữu ích cho việc đồng bộ hóa dữ liệu giữa các tab hoặc cửa sổ của trình duyệt.

## Tài Liệu
### Mục Đích
`StorageEvent` giúp lập trình viên theo dõi các thay đổi trong `localStorage` hoặc `sessionStorage`. Khi một thay đổi được thực hiện (như thêm, sửa đổi hoặc xóa một mục), sự kiện này sẽ được phát ra trên tất cả các tab hoặc cửa sổ đang mở của cùng một trang web.

### Cách Sử Dụng
Để lắng nghe sự kiện `StorageEvent`, bạn có thể sử dụng phương thức `window.addEventListener()`. Dưới đây là cú pháp cơ bản:

```javascript
window.addEventListener('storage', function(event) {
    console.log('Key:', event.key);
    console.log('Old Value:', event.oldValue);
    console.log('New Value:', event.newValue);
    console.log('Storage Area:', event.storageArea);
    console.log('URL:', event.url);
});
```

### Thông Tin Chi Tiết
- **Các thuộc tính của StorageEvent**:
  - `key`: Chìa khóa của mục đã được thay đổi.
  - `oldValue`: Giá trị trước khi thay đổi.
  - `newValue`: Giá trị mới sau khi thay đổi.
  - `url`: URL nơi sự kiện xảy ra.
  - `storageArea`: Khu vực lưu trữ (`localStorage` hoặc `sessionStorage`) mà sự kiện liên quan.

## Ví Dụ
### Ví dụ 1: Lắng Nghe Sự Kiện Storage
```javascript
window.addEventListener('storage', function(event) {
    console.log('Có sự thay đổi trong storage!');
    console.log('Chìa khóa:', event.key);
    console.log('Giá trị cũ:', event.oldValue);
    console.log('Giá trị mới:', event.newValue);
});
```

### Ví dụ 2: Thay Đổi Giá Trị
```javascript
// Trong tab 1
localStorage.setItem('username', 'JohnDoe'); // Sự kiện sẽ được phát ra trên tab khác

// Trong tab 2 (nơi lắng nghe sự kiện)
window.addEventListener('storage', function(event) {
    if (event.key === 'username') {
        console.log('Tên người dùng đã thay đổi thành:', event.newValue);
    }
});
```

## Giải Thích
### Những Lỗi Thường Gặp
- **Không nhận được sự kiện**: Nếu bạn thử thay đổi `localStorage` trong cùng một tab, sự kiện `StorageEvent` sẽ không được phát ra. Sự kiện này chỉ phát ra khi có thay đổi từ một tab khác.
- **Sử dụng sai khu vực lưu trữ**: Đảm bảo rằng bạn đang làm việc với `localStorage` hoặc `sessionStorage` một cách chính xác, vì chúng có những đặc điểm khác nhau.

### Ghi Chú Thêm
- `StorageEvent` không hỗ trợ trong một số trình duyệt cũ. Hãy kiểm tra tính tương thích trước khi triển khai.
- Các sự kiện có thể không xảy ra theo thứ tự nếu có nhiều thay đổi diễn ra liên tiếp.

## Tóm Tắt Một Câu
Sự kiện `StorageEvent` cho phép bạn theo dõi và xử lý các thay đổi trong `localStorage` và `sessionStorage` giữa các tab hoặc cửa sổ của trình duyệt trong JavaScript.