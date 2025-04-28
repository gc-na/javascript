<!--
Meta Description: # Opener trong JavaScript: Tính Năng và Cách Sử Dụng ## Tóm tắt Trong JavaScript, "opener" là một thuộc tính toàn cục của đối tượng `window`, cho phép...
Meta Keywords: cửa, cha, opener, window, con
-->

# Opener trong JavaScript: Tính Năng và Cách Sử Dụng

## Tóm tắt
Trong JavaScript, "opener" là một thuộc tính toàn cục của đối tượng `window`, cho phép bạn truy cập cửa sổ cha của một cửa sổ con. Điều này cực kỳ hữu ích trong các tình huống khi bạn cần tương tác giữa hai cửa sổ.

## Tài liệu
### Mục đích
`opener` cho phép bạn lấy thông tin và thực hiện thao tác trên cửa sổ cha từ một cửa sổ con. Nếu cửa sổ con được mở từ cửa sổ cha, bạn có thể sử dụng thuộc tính này để truy cập và điều khiển cửa sổ cha.

### Cách sử dụng
Khi bạn mở một cửa sổ mới bằng phương thức `window.open()`, cửa sổ mới đó có thể sử dụng thuộc tính `opener` để tham chiếu đến cửa sổ cha. Nếu cửa sổ con không có cửa sổ cha (ví dụ như khi nó được mở từ một tab mới), thuộc tính này sẽ trả về `null`.

```javascript
// Mở một cửa sổ mới
let newWindow = window.open('https://example.com');

// Trong cửa sổ con, bạn có thể truy cập cửa sổ cha như sau:
if (window.opener) {
    console.log('Cửa sổ cha:', window.opener);
} else {
    console.log('Không có cửa sổ cha.');
}
```

## Ví dụ
### Ví dụ 1: Truy cập thuộc tính của cửa sổ cha

```javascript
// Cửa sổ cha
let parentWindow = window.open('about:blank', 'parentWindow');

// Trong cửa sổ con
if (window.opener) {
    window.opener.document.title = 'Tiêu đề mới từ cửa sổ con';
}
```

### Ví dụ 2: Kiểm tra sự hiện diện của cửa sổ cha

```javascript
if (window.opener) {
    console.log('Cửa sổ cha tồn tại.');
} else {
    console.log('Không có cửa sổ cha.');
}
```

## Giải thích
Một số lưu ý quan trọng khi làm việc với `opener`:

1. **Bảo mật**: Nếu cửa sổ con được mở từ một miền khác (cross-origin), bạn sẽ không thể truy cập các thuộc tính của cửa sổ cha do chính sách bảo mật của trình duyệt (Same-Origin Policy).
2. **Đóng cửa sổ**: Nếu cửa sổ cha bị đóng, thuộc tính `opener` trong cửa sổ con sẽ vẫn giữ giá trị là tham chiếu đến cửa sổ cha, nhưng bạn sẽ không thể tương tác với nó.
3. **Kiểm tra null**: Luôn luôn kiểm tra xem `window.opener` có phải là `null` trước khi thực hiện các thao tác, để tránh lỗi.

## Tóm tắt một dòng
`opener` trong JavaScript là thuộc tính cho phép cửa sổ con truy cập và tương tác với cửa sổ cha của nó.