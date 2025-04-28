<!--
Meta Description: # Sự kiện onsubmit trong JavaScript: Hướng dẫn và Ví dụ ## Tóm tắt Sự kiện `onsubmit` trong JavaScript cho phép lập trình viên xử lý các hành động khi...
Meta Keywords: gửi, biểu, mẫu, onsubmit, kiện
-->

# Sự kiện onsubmit trong JavaScript: Hướng dẫn và Ví dụ

## Tóm tắt
Sự kiện `onsubmit` trong JavaScript cho phép lập trình viên xử lý các hành động khi một biểu mẫu (form) được gửi đi. Đây là một công cụ mạnh mẽ để kiểm tra dữ liệu nhập vào, ngăn chặn gửi biểu mẫu nếu có lỗi, hoặc thực hiện các thao tác khác trước khi dữ liệu được gửi đến máy chủ.

## Tài liệu
### Mục đích
Sự kiện `onsubmit` được sử dụng để xác định hành động cần thực hiện khi người dùng gửi biểu mẫu. Nó thường được sử dụng để kiểm tra dữ liệu người dùng và ngăn chặn việc gửi biểu mẫu nếu có lỗi.

### Cú pháp
Sự kiện `onsubmit` có thể được gán trực tiếp trong thẻ `<form>` hoặc thông qua JavaScript. Dưới đây là cú pháp cơ bản:

```html
<form onsubmit="return functionName();">
  <!-- Các trường nhập -->
  <input type="submit" value="Gửi">
</form>
```

### Sử dụng
Để sử dụng sự kiện `onsubmit`, bạn cần:
1. Xác định một hàm JavaScript để xử lý sự kiện.
2. Gán hàm này cho thuộc tính `onsubmit` của thẻ `<form>`.
3. Trong hàm, bạn có thể kiểm tra dữ liệu và trả về `true` để cho phép gửi biểu mẫu hoặc `false` để ngăn chặn.

### Chi tiết
- Sự kiện `onsubmit` xảy ra trước khi biểu mẫu được gửi đến máy chủ.
- Bạn có thể sử dụng `event.preventDefault()` để ngăn chặn hành vi mặc định của biểu mẫu.

## Ví dụ
### Ví dụ 1: Kiểm tra dữ liệu nhập
```html
<form onsubmit="return validateForm()">
  <label for="name">Tên:</label>
  <input type="text" id="name" name="name" required>
  <input type="submit" value="Gửi">
</form>

<script>
function validateForm() {
  var name = document.getElementById("name").value;
  if (name === "") {
    alert("Tên không được để trống.");
    return false; // Ngăn chặn gửi biểu mẫu
  }
  return true; // Cho phép gửi biểu mẫu
}
</script>
```

### Ví dụ 2: Ngăn chặn gửi biểu mẫu
```html
<form id="myForm">
  <input type="text" id="email" required>
  <input type="submit" value="Gửi">
</form>

<script>
document.getElementById("myForm").onsubmit = function(event) {
  event.preventDefault(); // Ngăn chặn gửi biểu mẫu
  alert("Gửi biểu mẫu đã bị ngăn chặn.");
}
</script>
```

## Giải thích
- **Ngăn chặn gửi biểu mẫu:** Khi bạn trả về `false` từ hàm `onsubmit` hoặc gọi `event.preventDefault()`, biểu mẫu sẽ không được gửi.
- **Hỗ trợ trình duyệt:** Sự kiện `onsubmit` được hỗ trợ trên tất cả các trình duyệt hiện đại, nhưng cần kiểm tra tính tương thích nếu sử dụng các tính năng JavaScript mới.
- **Truy cập dữ liệu:** Bạn có thể truy cập các trường nhập trong biểu mẫu thông qua `document.getElementById()` hoặc `this.elements`.

## Tóm tắt một câu
Sự kiện `onsubmit` trong JavaScript cho phép kiểm tra và xử lý dữ liệu trước khi gửi biểu mẫu, giúp nâng cao trải nghiệm người dùng và đảm bảo tính chính xác của dữ liệu.