<!--
Meta Description: # SharedStorage trong JavaScript: Tính Năng Chia Sẻ Dữ Liệu Giữa Các Tab ## Tóm tắt SharedStorage là một API trong JavaScript cho phép các tab hoặc cử...
Meta Keywords: sharedstorage, liệu, các, một, javascript
-->

# SharedStorage trong JavaScript: Tính Năng Chia Sẻ Dữ Liệu Giữa Các Tab

## Tóm tắt
SharedStorage là một API trong JavaScript cho phép các tab hoặc cửa sổ trình duyệt chia sẻ dữ liệu với nhau một cách dễ dàng và hiệu quả. Tính năng này giúp cải thiện trải nghiệm người dùng bằng cách đồng bộ hóa trạng thái và thông tin giữa các phiên làm việc.

## Tài liệu
### Mục đích
SharedStorage được thiết kế để giải quyết vấn đề chia sẻ dữ liệu giữa các tab, cửa sổ hoặc iframe trong cùng một trình duyệt. Điều này rất hữu ích cho các ứng dụng web hiện đại, nơi mà người dùng có thể mở nhiều tab cùng lúc và mong muốn các tab này đồng bộ hóa dữ liệu.

### Cách sử dụng
Để sử dụng SharedStorage, bạn cần kiểm tra xem trình duyệt có hỗ trợ tính năng này hay không. Sau đó, bạn có thể sử dụng các phương thức để thêm, xóa, và lắng nghe sự kiện thay đổi dữ liệu.

#### Cấu trúc cơ bản
```javascript
if ('SharedStorage' in window) {
    // Thực hiện các thao tác với SharedStorage
}
```

### Các phương thức chính
- **setItem(key, value)**: Lưu trữ một giá trị với một khóa nhất định.
- **getItem(key)**: Lấy giá trị tương ứng với khóa đã cho.
- **removeItem(key)**: Xóa dữ liệu tương ứng với khóa đã cho.
- **clear()**: Xóa tất cả dữ liệu trong SharedStorage.
- **onstorage**: Sự kiện được kích hoạt khi có sự thay đổi dữ liệu.

## Ví dụ
### Lưu trữ và lấy dữ liệu
```javascript
// Kiểm tra hỗ trợ SharedStorage
if ('sharedStorage' in window) {
    // Lưu trữ dữ liệu
    sharedStorage.setItem('username', 'JohnDoe');

    // Lấy dữ liệu
    const username = sharedStorage.getItem('username');
    console.log(username); // "JohnDoe"
}
```

### Lắng nghe sự kiện thay đổi
```javascript
if ('sharedStorage' in window) {
    sharedStorage.onstorage = (event) => {
        console.log(`Dữ liệu đã thay đổi: ${event.key} = ${event.newValue}`);
    };

    // Thay đổi dữ liệu
    sharedStorage.setItem('username', 'JaneDoe'); // Gọi sự kiện onstorage
}
```

## Giải thích
### Những cạm bẫy phổ biến
- **Hỗ trợ trình duyệt**: Không phải tất cả các trình duyệt đều hỗ trợ SharedStorage. Kiểm tra tính khả dụng trước khi sử dụng.
- **Giới hạn kích thước**: SharedStorage có giới hạn kích thước lưu trữ, vì vậy không nên lưu trữ dữ liệu quá lớn.
- **Thay đổi không đồng bộ**: Sự kiện onstorage có thể không được kích hoạt ngay lập tức, vì vậy cần lưu ý khi làm việc với dữ liệu gần như thời gian thực.

## Tóm tắt một dòng
SharedStorage là một API trong JavaScript cho phép chia sẻ dữ liệu giữa các tab và cửa sổ trình duyệt, giúp đồng bộ hóa trải nghiệm người dùng.