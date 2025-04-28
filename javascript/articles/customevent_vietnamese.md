<!--
Meta Description: # CustomEvent trong JavaScript: Cách Tạo và Sử Dụng Sự Kiện Tùy Chỉnh ## Tóm tắt `CustomEvent` là một đối tượng trong JavaScript cho phép bạn tạo ra c...
Meta Keywords: kiện, một, bạn, các, tùy
-->

# CustomEvent trong JavaScript: Cách Tạo và Sử Dụng Sự Kiện Tùy Chỉnh

## Tóm tắt
`CustomEvent` là một đối tượng trong JavaScript cho phép bạn tạo ra các sự kiện tùy chỉnh, có thể chứa thông tin bổ sung thông qua thuộc tính `detail`. Điều này giúp cho việc giao tiếp giữa các phần của ứng dụng trở nên linh hoạt hơn.

## Tài liệu
### Mục đích
`CustomEvent` được sử dụng để tạo ra các sự kiện tùy chỉnh mà bạn có thể phát ra từ các phần tử DOM. Nó cho phép bạn thêm thông tin chi tiết vào sự kiện thông qua thuộc tính `detail`, giúp các phần tử khác hoặc các hàm lắng nghe sự kiện có thể nhận biết và xử lý thông tin này.

### Cách sử dụng
Để tạo một `CustomEvent`, bạn có thể sử dụng cú pháp sau:

```javascript
let event = new CustomEvent(type, options);
```

- `type`: Tên của sự kiện (chuỗi).
- `options`: Một đối tượng tùy chọn với các thuộc tính:
  - `detail`: Thông tin bổ sung mà bạn muốn gửi kèm theo sự kiện.
  - `bubbles`: (tùy chọn) Xác định xem sự kiện có nổi bọt lên không (mặc định là `false`).
  - `cancelable`: (tùy chọn) Xác định xem sự kiện có thể bị hủy không (mặc định là `false`).

### Ví dụ
Dưới đây là một ví dụ cơ bản về cách tạo và phát ra một sự kiện tùy chỉnh:

```javascript
// Tạo một sự kiện tùy chỉnh
let myEvent = new CustomEvent('myCustomEvent', {
  detail: { message: 'Hello, World!' },
  bubbles: true,
  cancelable: true
});

// Lắng nghe sự kiện
document.addEventListener('myCustomEvent', function (e) {
  console.log(e.detail.message); // In ra: Hello, World!
});

// Phát ra sự kiện
document.dispatchEvent(myEvent);
```

## Giải thích
Khi làm việc với `CustomEvent`, một số điểm cần lưu ý là:

- **Nổi bọt**: Nếu bạn đặt thuộc tính `bubbles` thành `true`, sự kiện sẽ nổi bọt lên qua chuỗi DOM. Điều này có nghĩa là các phần tử cha cũng có thể lắng nghe sự kiện này.
- **Hủy**: Nếu bạn đặt thuộc tính `cancelable` thành `true`, bạn có thể hủy sự kiện trong một hàm lắng nghe bằng cách gọi `event.preventDefault()`.
- **Chi tiết**: Thông tin trong thuộc tính `detail` có thể là bất kỳ kiểu dữ liệu nào, bao gồm đối tượng, mảng, hay chuỗi, giúp bạn truyền tải thông tin một cách linh hoạt.

## Tóm tắt một dòng
`CustomEvent` cho phép bạn tạo ra các sự kiện tùy chỉnh trong JavaScript, giúp việc giao tiếp giữa các phần tử và chức năng trong ứng dụng trở nên linh hoạt hơn.