<!--
Meta Description: # FormData trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ Sử Dụng ## Tóm tắt `FormData` là một đối tượng trong JavaScript cho phép dễ dàng xây dựng và ...
Meta Keywords: formdata, một, liệu, key, value
-->

# FormData trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ Sử Dụng

## Tóm tắt
`FormData` là một đối tượng trong JavaScript cho phép dễ dàng xây dựng và gửi dữ liệu biểu mẫu (form data) thông qua AJAX hoặc Fetch API mà không cần phải chuyển đổi thủ công dữ liệu thành định dạng URL-encoded.

## Tài liệu
### Mục đích
`FormData` được sử dụng để tạo ra một đối tượng chứa các cặp key-value từ một biểu mẫu HTML, cho phép bạn gửi dữ liệu một cách dễ dàng tới server mà không cần phải lo lắng về việc mã hóa dữ liệu.

### Cách sử dụng
Để sử dụng `FormData`, bạn có thể khởi tạo nó từ một biểu mẫu HTML hoặc thêm các giá trị thủ công. Dưới đây là cú pháp cơ bản:

```javascript
const formData = new FormData(formElement);
```

Trong đó `formElement` là một tham chiếu đến phần tử `<form>` trong tài liệu HTML.

### Chi tiết
- **Khởi tạo**: Có thể khởi tạo `FormData` từ một phần tử `<form>` hoặc bằng cách thêm các cặp key-value bằng phương thức `append()`.
- **Phương thức**: Một số phương thức quan trọng bao gồm:
  - `append(name, value)`: Thêm một cặp key-value vào `FormData`.
  - `delete(name)`: Xóa một cặp key-value từ `FormData`.
  - `get(name)`: Lấy giá trị của key cụ thể.
  - `has(name)`: Kiểm tra xem key có tồn tại hay không.
  - `set(name, value)`: Thiết lập giá trị cho key, nếu key đã tồn tại, giá trị cũ sẽ bị thay thế.

## Ví dụ
### Ví dụ cơ bản
```html
<form id="myForm">
    <input type="text" name="username" value="JohnDoe">
    <input type="email" name="email" value="john@example.com">
    <input type="file" name="profilePic">
</form>

<script>
    const formElement = document.getElementById('myForm');
    const formData = new FormData(formElement);

    // Gửi dữ liệu qua Fetch API
    fetch('https://example.com/api/upload', {
        method: 'POST',
        body: formData
    });
</script>
```

### Ví dụ thêm dữ liệu thủ công
```javascript
const formData = new FormData();
formData.append('username', 'JaneDoe');
formData.append('email', 'jane@example.com');

// Gửi dữ liệu
fetch('https://example.com/api/register', {
    method: 'POST',
    body: formData
});
```

## Giải thích
- **Điểm cần lưu ý**: Khi sử dụng `FormData`, bạn không cần phải chỉ định `Content-Type` cho yêu cầu vì trình duyệt sẽ tự động thiết lập nó cho bạn, bao gồm cả ranh giới multipart nếu có tệp đính kèm.
- **Trình duyệt hỗ trợ**: `FormData` được hỗ trợ trên hầu hết các trình duyệt hiện đại, nhưng nên kiểm tra tính tương thích nếu bạn cần hỗ trợ các trình duyệt cũ hơn.
- **Giới hạn kích thước**: Hãy nhớ rằng có giới hạn về kích thước cho các yêu cầu POST tùy thuộc vào server mà bạn đang làm việc.

## Tóm tắt một dòng
`FormData` là một đối tượng JavaScript dùng để dễ dàng xây dựng và gửi dữ liệu biểu mẫu qua AJAX hoặc Fetch API.