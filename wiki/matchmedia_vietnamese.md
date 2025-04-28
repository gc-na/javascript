<!--
Meta Description: # Sử Dụng matchMedia trong JavaScript: Hướng Dẫn Chi Tiết ## Tóm Tắt `matchMedia` là một phương thức trong JavaScript cho phép bạn kiểm tra và lắng ng...
Meta Keywords: media, query, các, điều, một
-->

# Sử Dụng matchMedia trong JavaScript: Hướng Dẫn Chi Tiết

## Tóm Tắt
`matchMedia` là một phương thức trong JavaScript cho phép bạn kiểm tra và lắng nghe các thay đổi về kích thước màn hình và các điều kiện CSS media queries.

## Tài Liệu
Phương thức `matchMedia` được định nghĩa trong đối tượng `window`. Nó cho phép bạn thiết lập các điều kiện media query và nhận thông tin về việc điều kiện đó có được thỏa mãn hay không.

### Mục Đích
- Kiểm tra xem một media query cụ thể có đang được thỏa mãn hay không.
- Lắng nghe và phản hồi các thay đổi về điều kiện media query.

### Cú Pháp
```javascript
const mediaQueryList = window.matchMedia(mediaQueryString);
```

- `mediaQueryString`: Một chuỗi chứa điều kiện media query (ví dụ: `(max-width: 600px)`).

### Trả Về
- Phương thức `matchMedia` trả về một đối tượng `MediaQueryList`, bao gồm các thuộc tính và phương thức để kiểm tra trạng thái của media query.

### Các Thuộc Tính
- `matches`: Trả về `true` nếu media query được thỏa mãn, ngược lại trả về `false`.
- `media`: Trả về chuỗi media query đã được kiểm tra.
- `addListener(callback)`: Thêm một hàm lắng nghe để phản hồi khi điều kiện media query thay đổi (đã được thay thế bằng `addEventListener` trong các trình duyệt hiện đại).
- `removeListener(callback)`: Xóa một hàm lắng nghe trước đó (đã được thay thế bằng `removeEventListener`).

### Ví dụ Sử Dụng
```javascript
// Kiểm tra xem màn hình có kích thước nhỏ hơn 600px không
const mediaQueryList = window.matchMedia('(max-width: 600px)');

if (mediaQueryList.matches) {
    console.log('Màn hình nhỏ hơn 600px');
} else {
    console.log('Màn hình lớn hơn hoặc bằng 600px');
}

// Lắng nghe thay đổi media query
const handleMediaChange = (event) => {
    if (event.matches) {
        console.log('Màn hình nhỏ hơn 600px');
    } else {
        console.log('Màn hình lớn hơn hoặc bằng 600px');
    }
};

mediaQueryList.addEventListener('change', handleMediaChange);
```

## Giải Thích
Một số điều cần lưu ý khi sử dụng `matchMedia`:
- **Trình Duyệt Hỗ Trợ**: Một số trình duyệt cũ có thể không hỗ trợ `addListener` và `removeListener`. Thay vào đó, bạn có thể sử dụng `addEventListener` và `removeEventListener`.
- **Hiệu Suất**: Việc lắng nghe nhiều media queries có thể làm tăng hiệu suất. Hãy đảm bảo chỉ lắng nghe những điều bạn thực sự cần.
- **Thay Đổi Kích Thước**: Khi bạn thay đổi kích thước cửa sổ, các sự kiện sẽ được kích hoạt dựa trên các điều kiện media query đã thiết lập.

## Tóm Tắt Một Dòng
`matchMedia` trong JavaScript cho phép kiểm tra và lắng nghe các điều kiện media query, hỗ trợ việc xây dựng giao diện responsive.