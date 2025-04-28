<!--
Meta Description: # HTMLFormControlsCollection trong JavaScript: Hướng dẫn Chi tiết và Ví dụ ## Tóm tắt HTMLFormControlsCollection là một đối tượng trong JavaScript, ch...
Meta Keywords: điều, khiển, các, một, trong
-->

# HTMLFormControlsCollection trong JavaScript: Hướng dẫn Chi tiết và Ví dụ

## Tóm tắt
HTMLFormControlsCollection là một đối tượng trong JavaScript, cho phép truy cập và quản lý các điều khiển của một biểu mẫu HTML như input, select và textarea, giúp lập trình viên dễ dàng thao tác với các thành phần này trong quá trình phát triển ứng dụng web.

## Tài liệu
HTMLFormControlsCollection là một tập hợp các điều khiển (controls) liên quan đến một biểu mẫu HTML. Đối tượng này được tạo ra khi bạn truy cập thuộc tính `elements` của một đối tượng Form, chứa tất cả các phần tử con như input, select, textarea mà có thể được sử dụng trong việc thu thập dữ liệu từ người dùng.

### Mục đích
Mục đích chính của HTMLFormControlsCollection là cung cấp một cách đơn giản và hiệu quả để truy cập và thao tác với các điều khiển trong một biểu mẫu. Điều này rất hữu ích trong việc lập trình các chức năng như xác thực dữ liệu, thu thập thông tin từ người dùng và cập nhật giao diện.

### Cách sử dụng
Để sử dụng HTMLFormControlsCollection, bạn cần có một đối tượng Form. Bạn có thể truy cập các điều khiển bằng cách sử dụng thuộc tính `elements` của đối tượng Form đó. Dưới đây là cú pháp cơ bản:

```javascript
let form = document.getElementById('myForm');
let controls = form.elements;
```

### Chi tiết
- **Đặc điểm**: Đối tượng HTMLFormControlsCollection có thể chứa nhiều loại điều khiển như `<input>`, `<select>`, `<textarea>`, và `<button>`.
- **Truy cập**: Bạn có thể truy cập các điều khiển bằng chỉ số (index) hoặc tên (name) của chúng. Ví dụ: `controls[0]` hoặc `controls['username']`.
- **Duyệt qua**: Để duyệt qua tất cả các điều khiển trong HTMLFormControlsCollection, bạn có thể sử dụng vòng lặp `for` hoặc `forEach`.

## Ví dụ
### Ví dụ 1: Truy cập các điều khiển trong biểu mẫu
```html
<form id="myForm">
  <input type="text" name="username" />
  <input type="password" name="password" />
  <input type="submit" value="Đăng nhập" />
</form>

<script>
  let form = document.getElementById('myForm');
  let controls = form.elements;

  console.log(controls['username'].value); // In giá trị của input username
</script>
```

### Ví dụ 2: Duyệt qua tất cả các điều khiển
```javascript
let form = document.getElementById('myForm');
let controls = form.elements;

for (let i = 0; i < controls.length; i++) {
  console.log(controls[i].name + ': ' + controls[i].value);
}
```

## Giải thích
Khi làm việc với HTMLFormControlsCollection, có một số lưu ý mà bạn cần chú ý:
- **Lỗi khi truy cập**: Nếu bạn cố gắng truy cập một điều khiển không tồn tại, bạn sẽ nhận được giá trị `undefined`. Hãy chắc chắn rằng tên hoặc chỉ số mà bạn đang sử dụng là chính xác.
- **Thay đổi giá trị**: Khi bạn thay đổi giá trị của một điều khiển, giá trị này sẽ không được cập nhật trong HTML cho đến khi bạn thực hiện thao tác với sự kiện (như submit).
- **Phân loại điều khiển**: Không phải tất cả các loại điều khiển đều có thuộc tính giống nhau. Ví dụ, các điều khiển checkbox và radio có thuộc tính `checked`, trong khi các điều khiển text không có.

## Tóm tắt một dòng
HTMLFormControlsCollection là một công cụ mạnh mẽ trong JavaScript cho phép lập trình viên dễ dàng truy cập và quản lý các điều khiển trong biểu mẫu HTML.