<!--
Meta Description: # Sự kiện HashChangeEvent trong JavaScript: Hiểu Biết và Ứng Dụng ## Tóm Tắt Sự kiện `HashChangeEvent` trong JavaScript cho phép bạn theo dõi sự thay ...
Meta Keywords: hash, kiện, trong, dụng, url
-->

# Sự kiện HashChangeEvent trong JavaScript: Hiểu Biết và Ứng Dụng

## Tóm Tắt
Sự kiện `HashChangeEvent` trong JavaScript cho phép bạn theo dõi sự thay đổi của phần hash trong URL, giúp xây dựng các ứng dụng web một cách linh hoạt mà không cần tải lại trang.

## Tài Liệu
### Mục Đích
`HashChangeEvent` được sử dụng để lắng nghe và xử lý các thay đổi trong phần hash của URL. Điều này rất hữu ích trong các ứng dụng một trang (SPA) nơi bạn muốn cập nhật nội dung mà không làm mới trang.

### Cách Sử Dụng
Để sử dụng `HashChangeEvent`, bạn cần đăng ký một sự kiện lắng nghe cho `window` khi hash trong URL thay đổi. Sự kiện này sẽ được kích hoạt mỗi khi phần hash của URL thay đổi.

#### Cú pháp
```javascript
window.addEventListener("hashchange", function(event) {
    // Xử lý sự kiện
});
```

### Chi Tiết
- **Thuộc Tính**: `HashChangeEvent` có thuộc tính `newURL` và `oldURL` để lấy URL trước và sau khi thay đổi.
- **Trình duyệt hỗ trợ**: Hầu hết các trình duyệt hiện đại đều hỗ trợ `HashChangeEvent`, nhưng bạn nên kiểm tra khả năng tương thích nếu cần hỗ trợ cho trình duyệt cũ.

## Ví Dụ
### Ví dụ Cơ Bản
```javascript
window.addEventListener("hashchange", function(event) {
    console.log("Địa chỉ URL cũ: " + event.oldURL);
    console.log("Địa chỉ URL mới: " + event.newURL);
});

// Thay đổi hash
window.location.hash = 'new-section';
```

### Ví dụ với Hàm Điều Hướng
```javascript
function navigateToSection(section) {
    window.location.hash = section;
}

window.addEventListener("hashchange", function(event) {
    const currentSection = window.location.hash.substring(1);
    console.log("Đang chuyển tới: " + currentSection);
});

// Gọi hàm điều hướng
navigateToSection('home');
```

## Giải Thích
### Những Lỗi Thường Gặp
1. **Không Được Kích Hoạt**: Nếu bạn không thấy sự kiện `hashchange` được kích hoạt, hãy đảm bảo rằng bạn đang thay đổi hash sau khi đăng ký sự kiện.
2. **Trình duyệt Không Hỗ Trợ**: Một số trình duyệt cũ có thể không hỗ trợ sự kiện này. Kiểm tra khả năng tương thích là điều cần thiết.

### Lưu Ý
- Sử dụng `HashChangeEvent` là một cách tốt để quản lý lịch sử và điều hướng trong ứng dụng SPA mà không cần tải lại trang.
- Hãy cẩn thận khi làm việc với các URL phức tạp, vì có thể xảy ra xung đột khi các phần hash giống nhau nhưng đường dẫn khác nhau.

## Tóm Tắt Một Dòng
Sự kiện `HashChangeEvent` trong JavaScript cho phép theo dõi và xử lý các thay đổi trong phần hash của URL, hỗ trợ việc phát triển ứng dụng web một cách linh hoạt và mượt mà.