<!--
Meta Description: # DOMStringMap trong JavaScript: Hướng dẫn chi tiết ## Tóm tắt DOMStringMap là một đối tượng trong JavaScript cho phép quản lý các thuộc tính dữ liệu ...
Meta Keywords: thuộc, tính, các, trong, data
-->

# DOMStringMap trong JavaScript: Hướng dẫn chi tiết

## Tóm tắt
DOMStringMap là một đối tượng trong JavaScript cho phép quản lý các thuộc tính dữ liệu tùy chỉnh được lưu trữ trong các phần tử HTML thông qua thuộc tính `data-*`.

## Tài liệu
### Mục đích
DOMStringMap dùng để truy cập và quản lý các thuộc tính dữ liệu được định nghĩa với tiền tố `data-` trong HTML. Nó giúp lập trình viên dễ dàng lưu trữ và lấy thông tin mà không cần phải sử dụng các thuộc tính HTML truyền thống.

### Cách sử dụng
Khi một phần tử HTML có thuộc tính `data-*`, nó được ánh xạ thành một thuộc tính trong đối tượng DOMStringMap. Ví dụ, nếu bạn có một phần tử như sau:

```html
<div id="myElement" data-user-id="123" data-user-name="John"></div>
```

Bạn có thể truy cập các giá trị này thông qua JavaScript như sau:

```javascript
const element = document.getElementById('myElement');
const dataMap = element.dataset;

console.log(dataMap.userId); // "123"
console.log(dataMap.userName); // "John"
```

### Chi tiết
- **Loại dữ liệu**: Các thuộc tính trong DOMStringMap luôn là chuỗi (string).
- **Chuyển đổi thuộc tính**: Các ký tự gạch dưới (`_`) trong tên thuộc tính sẽ được chuyển thành chữ hoa. Ví dụ, `data-user-id` trở thành `userId`.
- **Khả năng mở rộng**: Bạn có thể thêm các thuộc tính `data-*` tùy chỉnh vào bất kỳ phần tử nào trong HTML mà không làm thay đổi cấu trúc của trang.

## Ví dụ
### Ví dụ 1: Lấy dữ liệu từ DOMStringMap

```html
<div id="profile" data-age="30" data-location="Hanoi"></div>

<script>
  const profile = document.getElementById('profile');
  console.log(profile.dataset.age); // "30"
  console.log(profile.dataset.location); // "Hanoi"
</script>
```

### Ví dụ 2: Thay đổi giá trị thuộc tính

```html
<div id="settings" data-theme="light"></div>

<script>
  const settings = document.getElementById('settings');
  settings.dataset.theme = "dark"; // Thay đổi theme thành "dark"
  console.log(settings.dataset.theme); // "dark"
</script>
```

## Giải thích
### Cạm bẫy thường gặp
- **Lỗi chính tả**: Đảm bảo rằng tên thuộc tính trong HTML và khi truy cập bằng JavaScript phải chính xác.
- **Định dạng dữ liệu**: Tất cả các giá trị trong DOMStringMap là chuỗi. Nếu bạn cần giá trị số, bạn phải chuyển đổi bằng cách sử dụng `parseInt()` hoặc `parseFloat()`.

### Ghi chú bổ sung
- DOMStringMap không hỗ trợ các thuộc tính không tồn tại, nếu bạn truy cập vào một thuộc tính không được định nghĩa, nó sẽ trả về `undefined`.

## Tóm tắt một dòng
DOMStringMap trong JavaScript cho phép bạn dễ dàng quản lý và truy cập các thuộc tính dữ liệu tùy chỉnh từ các phần tử HTML thông qua thuộc tính `data-*`.