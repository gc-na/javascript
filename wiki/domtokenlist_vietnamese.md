<!--
Meta Description: # DOMTokenList trong JavaScript: Hiểu Biết và Ứng Dụng ## Tóm Tắt DOMTokenList là một đối tượng trong JavaScript cho phép quản lý danh sách các token ...
Meta Keywords: token, các, domtokenlist, một, element
-->

# DOMTokenList trong JavaScript: Hiểu Biết và Ứng Dụng

## Tóm Tắt
DOMTokenList là một đối tượng trong JavaScript cho phép quản lý danh sách các token (chuỗi) trong thuộc tính class của phần tử HTML. Điều này giúp dễ dàng thêm, xóa và kiểm tra các lớp CSS trên các phần tử DOM.

## Tài Liệu
### Mục Đích
DOMTokenList cung cấp một cách hiệu quả và tiện lợi để thao tác với danh sách các lớp CSS của phần tử DOM. Thông qua đối tượng này, lập trình viên có thể thực hiện các thao tác như thêm, xóa và kiểm tra sự tồn tại của các lớp mà không cần phải xử lý chuỗi thủ công.

### Cách Sử Dụng
Đối tượng DOMTokenList thường được trả về bởi các thuộc tính như `classList` của phần tử HTML. Các phương thức chính của DOMTokenList bao gồm:

- **add(token)**: Thêm một hoặc nhiều token vào danh sách.
- **remove(token)**: Xóa một hoặc nhiều token khỏi danh sách.
- **toggle(token, force)**: Thay đổi trạng thái của token. Nếu token không có, nó sẽ được thêm; nếu có, nó sẽ bị xóa. Tham số `force` cho phép điều khiển hành động thêm hoặc xóa.
- **contains(token)**: Kiểm tra xem token có tồn tại trong danh sách hay không.

### Chi Tiết
- **Trả Về**: DOMTokenList là một đối tượng có kiểu danh sách, cho phép truy cập theo chỉ số.
- **Tính Năng**: Hỗ trợ thêm hoặc xóa nhiều token cùng một lúc bằng cách truyền vào nhiều tham số.
- **Tương Thích**: DOMTokenList được hỗ trợ trên hầu hết tất cả các trình duyệt hiện đại.

## Ví Dụ
### Thêm Lớp CSS
```javascript
const element = document.getElementById('myElement');
element.classList.add('new-class');
```

### Xóa Lớp CSS
```javascript
const element = document.getElementById('myElement');
element.classList.remove('old-class');
```

### Kiểm Tra Sự Tồn Tại
```javascript
const element = document.getElementById('myElement');
if (element.classList.contains('active')) {
    console.log('Element is active');
}
```

### Thay Đổi Trạng Thái Lớp
```javascript
const element = document.getElementById('myElement');
element.classList.toggle('visible');
```

## Giải Thích
- **Nhầm Lẫn với Chuỗi**: Một số lập trình viên có thể nhầm lẫn giữa DOMTokenList và chuỗi. DOMTokenList cung cấp phương thức để thao tác trực tiếp, trong khi chuỗi yêu cầu phải xử lý thủ công.
- **Không Tương Thích với IE10 trở về trước**: Các phiên bản Internet Explorer cũ hơn không hỗ trợ DOMTokenList, điều này có thể gây ra vấn đề nếu cần phải phát triển ứng dụng tương thích với các trình duyệt này.
- **Thao Tác Nhiều Token**: Khi thêm hoặc xóa nhiều token, bạn có thể truyền vào nhiều tham số, ví dụ: `element.classList.add('class1', 'class2')`.

## Tóm Tắt Một Dòng
DOMTokenList trong JavaScript là một công cụ mạnh mẽ giúp quản lý các lớp CSS của phần tử DOM một cách dễ dàng và hiệu quả.